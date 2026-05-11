Secure Reactive Microservices with Spring Cloud Gateway 🔐

This example is built with Spring Cloud Gateway and Spring WebFlux to show reactive microservices. See Secure Reactive Microservices with Spring Cloud Gateway to how it was created.

Prerequisites: Java 11 and an internet connection.

Getting Started
Links
Help
License
Getting Started

To install this example, run the following commands:

git clone https://github.com/oktadev/java-microservices-examples.git
cd java-microservices-examples/spring-cloud-gateway
The api-gateway and car-service projects are already pre-configured to be locked down with OAuth 2.0 and Okta. That means if you try to run them, you won't be able to login until you create an account, and an application in it.

If you already have an Okta account, see the Create a Web Application in Okta section below. Otherwise, we created a Maven plugin that configures a free Okta developer account + an OIDC app (in under a minute!).

To use it, run ./mvnw com.okta:okta-maven-plugin:setup to create an account and configure the gateway to work with Okta.

Copy the okta.* properties from the gateway's src/main/resources/application.properties to the same file in the car-service project.

Then, run all the projects with ./mvnw in separate terminal windows. You should be able to navigate to http://localhost:8761 and see the apps have been registered with Eureka.

Then, navigate to http://localhost:8080/cars in your browser, log in with Okta, and see the resulting JSON.

Create a Web Application in Okta

Log in to your Okta Developer account (or sign up if you don't have an account).

From the Applications page, choose Add Application.
On the Create New Application page, select Web.
Give your app a memorable name, add http://localhost:8080/login/oauth2/code/okta as a Login redirect URI and click Done.
Copy the issuer (found under API > Authorization Servers), client ID, and client secret into the application.properties of the api-gateway and car-service projects.

okta.oauth2.issuer=https://{yourOktaDomain}/oauth2/default
okta.oauth2.client-id=$clientId
okta.oauth2.client-secret=$clientSecret
Links

These examples uses the following open source libraries:

Okta Spring Boot Starter
Spring Boot
Spring Cloud
Spring Cloud Gateway
Spring Security
OpenJDK
Help

Please post any questions as comments on this example's blog post, or on the Okta Developer Forums.

License

Apache 2.0, see LICENSE.