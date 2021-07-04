## Spring Security with OAuth2 ##

**OAuth** is an authorization framework superseding it first version OAuth, created back in 2006. It defines the authorization flows between clients and one or more HTTP services in order to gain access to protected resources.

**OAuth2** defines the following server-side roles:

- **Resource Owner**: The service responsible for controlling resources’ access
- **Resource Server**: The service who actually supplies the resources
- **Authorization Server**: The service handling authorization process acting as a middleman between client and resource owner

### Pos ###

- Provides a stateless authorization system for stateless REST protocol
- Fits well in a micro-service architecture in which multiple resource servers can share a single authorization server
- Token content easy to manage on client’s side due to JSON format

### Cons ###

- A stateless protocol doesn’t permit access revocation on the server side
- Fixed lifetime for token add additional complexity for managing long-running sessions without compromising security (e.g. refresh token)
- A requirement for a secure store for a token on the client side

### The simplified flow ###
1. Authorization request is sent from client to server (acting as resource owner) using password authorization grant
1. Access token is returned to the client (along with refresh token)
1. Access token is then sent from client to server (acting as resource server) on each request for protected resource access
1. Server responds with required protected resources

![spring-security-oauth2](https://user-images.githubusercontent.com/86511913/124373234-b6924880-dcba-11eb-8cfa-a18de4974abd.png)

### Configuring security with oauth2 in spring boot ###
**1. Library must be used**

    <dependency>
        <groupId>org.springframework.security.oauth</groupId>
        <artifactId>spring-security-oauth2</artifactId>
    </dependency>
**2.@EnableAuthorizationServer**
