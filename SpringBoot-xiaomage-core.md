# 版本问题

Spring Boot 1.x版本  对应 Spring Framework版本 4.x版本	JDK版本1.8+

Spring Boot 2.x版本  对应 Spring Framework版本 5.x版本	JDK版本1.6+

读官方文档：https://docs.spring.io/spring-boot/docs/2.1.18.RELEASE/reference/html/getting-started-first-application.html#getting-started-first-application-executable-jar



# Spring Session

在pom.xml中加入spring-session依赖

~~~xml
        <dependency>
            <groupId>org.springframework.session</groupId>
            <artifactId>spring-session-data-redis</artifactId>
        </dependency>
        <!-- lettuce[ˈletɪs]：莴苣；生菜/客户端连接方式也可以换成jedis -->
        <dependency>
            <groupId>io.lettuce</groupId>
            <artifactId>lettuce-core</artifactId>
        </dependency>
		
        <!-- data-redis-starter 整合了redis，自动装配，redis2.0版本后底层用的lettuce NIO模式连接 -->
        <!--<dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-redis</artifactId>
        </dependency>-->
		<!--<dependency>
            <groupId>redis.clients</groupId>
            <artifactId>jedis</artifactId>
        </dependency>-->

        <!-- spring-session-core/spring-data-redis已经被spring-session-data-redis整合
 			所以不需要再单独引入-->
        <!--<dependency>
            <groupId>org.springframework.session</groupId>
            <artifactId>spring-session-core</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.data</groupId>
            <artifactId>spring-data-redis</artifactId>
        </dependency>-->

        <!--<dependency>
            <groupId>org.springframework.session</groupId>
            <artifactId>spring-session</artifactId>
            <version>1.3.5.RELEASE</version>
        </dependency>-->
~~~



# 独立的Spring应用



# 固化的Maven依赖



# 嵌入式Web容器



# 理解自动装配

激活自动装配的注解`@EnableAutoConfiguration`和`@SpringBootApplication`，将两者二选一标注在`@Configuration`类上。

`@SpringBootApplication`被用于激活 `@EnableAutoConfiguration、@ComponentScan和@Configuration`三个注解的特性。

- `@EnableAutoConfiguration`负责激活SpringBoot自动装配机制
- `@ComponentScan`激活 `@Component`的扫描
- `@Configuration`声明被标注为配置类

Spring Boot 1.4开始，`@SpringBootApplication注解不再标注@Configuration，而是@SpringBootConfiguration`。

这是类似于对象之间的继承关系，可以称之为“多层次@Component 派生性”。简言之，`@Configuration注解上标注了@Component`。因此，三者之间的层次关系如下：

- `@Component`
  - `@Configuration`
    - `@SpringBootApplication`

`@SpringBootApplication`是一个聚合注解



`@SpringBootApplication`继承`@Configuration` CGLIB提升特性。



# 整合模块

## JSON WEB TOKEN

1、导入jwt的依赖

~~~xml
		<!-- JWT Token认证 一般java用这个依赖-->
        <dependency>
            <groupId>com.auth0</groupId>
            <artifactId>java-jwt</artifactId>
            <version>3.10.3</version>
        </dependency>
		<!-- 这个版本的依赖也有在用，但是2018年7月之后没有再更新 -->
        <dependency>
            <groupId>io.jsonwebtoken</groupId>
            <artifactId>jjwt</artifactId>
            <version>0.9.1</version>
        </dependency>
~~~

2、编写JWT工具类

~~~java
//包括生成token令牌（签名）、校验令牌（验签）
public class JWTUtils {

    private static final String SIGN = "1qaz@WSX#EDC";

    /**
     * 签名 生成token
     *
     * @param user
     * @return
     */
    public static String sign(User user) {
        // head.payLoad.signature
        HashMap map = new HashMap();
        map.put("username", user.getUsername());
        map.put("password", user.getPassword());
        Calendar calendar = Calendar.getInstance();
        calendar.set(Calendar.SECOND, 2000);
        String sign = JWT.create()
                .withClaim("user", map)
                .withExpiresAt(calendar.getTime())//过期时间
                .sign(Algorithm.HMAC256(SIGN));//密钥签名
        return sign;
    }

    /**
     * 验签
     *
     * @param token
     * @return
     */
    public static Map<String, Claim> verify(String token) {
        // 验签 根据 HS256算法 私玥 验签token
        JWTVerifier verifier = JWT.require(Algorithm.HMAC256(SIGN)).build();
        DecodedJWT verify = verifier.verify(token);
        Map<String, Claim> claims = verify.getClaims();
        return claims;
    }

}
~~~

3、新增验证拦截器`AuthenticationInterceptor implements HandlerInterceptor `

~~~java
/**
 * @program: uncle-springboot
 * @description: 认证拦截器
 * @author: lei pei
 * @create: 2020-11-24 23:04
 */
public class AuthenticationInterceptor implements HandlerInterceptor {
    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        HandlerMethod method = (HandlerMethod) handler;
        Annotation annotation = method.getMethodAnnotation(GetMapping.class);
        //token一般放在请求头里，更安全
        String token = request.getHeader("token");
        try {
            JWTUtils.verify(token);
        } catch (TokenExpiredException tokenExpiredException) {
            throw new ApiException(400, "token已经过期");
        } catch (SignatureVerificationException signatureVerificationException) {
            throw new ApiException(400, "签名验证不通过");
        } catch (AlgorithmMismatchException algorithmMismatchException) {
            throw new ApiException(400, "生成token的算法不匹配");
        } catch (NullPointerException nullPointerException) {
            throw new ApiException(400, "token不存在");
        } catch (Exception exception) {
            throw new ApiException(400, exception.getMessage());
        }
//        response.setContentType("application/json;charset=UTF-8");
//        response.getWriter().println();
        return true;
    }
}
~~~



4、配置拦截器，新增一个InterceptorConfig配置类 实现WebMvcConfigurer，实现addInterceptors方法

~~~java
/**
 * @program: uncle-springboot
 * @description:
 * @author: lei pei
 * @create: 2020-11-29 21:27
 */
@Configuration
public class InterceptorConfig implements WebMvcConfigurer {
    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(new AuthenticationInterceptor())
                .addPathPatterns("/**")//拦截
                .excludePathPatterns("/user/login");//放行
    }
}
~~~

















