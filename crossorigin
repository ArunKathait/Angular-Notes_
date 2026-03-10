
 Global CORS Configuration (Better Approach)

Instead of writing @CrossOrigin in every controller, we can create a config class.

@Configuration
public class CorsConfig {

    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurer() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/**")
                        .allowedOrigins("http://localhost:4200")
                        .allowedMethods("*");
            }
        };
    }
}

1️⃣ Why we need CORS

When your Angular frontend runs, it usually runs on:

http://localhost:4200

Your Spring Boot backend runs on:

http://localhost:8080

Now when Angular tries to call an API:

http://localhost:8080/users

The browser blocks the request.

Why?

Because of CORS (Cross-Origin Resource Sharing).

Different ports = different origin.

4200  ≠  8080

So the browser thinks:

"This request might be unsafe."

So it blocks it.

2️⃣ What CORS configuration does

CORS configuration tells the backend:

Allow requests from Angular

So Spring Boot says:

Yes, Angular (localhost:4200) can access my APIs.

3️⃣ Why not use @CrossOrigin everywhere?

We could do this:

@CrossOrigin(origins="http://localhost:4200")
@RestController
public class UserController

But imagine you have 10 controllers:

UserController
StudentController
OrderController
ProductController

You would have to write @CrossOrigin 10 times.

That is not clean.

So we create one global configuration class.

4️⃣ What this configuration class does
@Configuration
public class CorsConfig
Meaning

This class is used for Spring configuration.

Spring reads it during application startup.

5️⃣ What @Bean does
@Bean
public WebMvcConfigurer corsConfigurer()

Meaning

We are telling Spring:

Create a configuration object

This object customizes Spring MVC behaviour.

6️⃣ What WebMvcConfigurer is

WebMvcConfigurer is an interface in Spring.

It allows us to customize Spring MVC settings like:

CORS
Interceptors
Formatters

Here we override the CORS configuration.

7️⃣ What this method does
addCorsMappings(CorsRegistry registry)

This method tells Spring:

Which requests are allowed

8️⃣ Important line
registry.addMapping("/**")

Meaning:

Apply CORS to ALL APIs

Example:

/users
/products
/orders
/students

All are allowed.

9️⃣ Allowed Origin
.allowedOrigins("http://localhost:4200")

Meaning:

Allow requests from Angular app

🔟 Allowed Methods
.allowedMethods("*")

Meaning:

Allow all HTTP methods:

GET
POST
PUT
DELETE
PATCH

1️⃣1️⃣ Final Flow
Angular (localhost:4200)
        ↓
HTTP request
        ↓
Spring Boot checks CORS config
        ↓
Request allowed
        ↓
Controller executes

1️⃣2️⃣ Why companies prefer this approach

Because:

One configuration
Works for entire application
Clean architecture

Instead of:

@CrossOrigin in every controller

1️⃣3️⃣ Simple Real-World Analogy

Think of your backend as a building.

Without CORS:

Security guard blocks everyone

With CORS:

Security guard allows only Angular app

1️⃣4️⃣ Important Interview Answer

If interviewer asks:

Why do we use CORS configuration in Spring Boot?

You can answer:

CORS configuration allows frontend applications like Angular running on a different origin to access Spring Boot REST APIs securely.
