## 2022
### Question 1:

> The `ServletRequest` interface is defined by the Java API documentation as “an object to provide client request information to a servlet”. Discuss any three methods of this interface that you are familiar with.

#### `setAttribute(String name, Object object)


**Description:**
The setAttribute method of the ServletRequest interface sets an attribute to a server, this is generally used to pass data around the server.

**Usage:**
``` java
request.setAttribute(String name, Object object)
```

#### `getParameter(String name)`

**Description:**
The getParameter method of the ServletRequest interface is used to retrieve data from a clients request. These parameters are typically part of a query string in a GET request or form data in a POST request.

**Usage:**
```java
request.getParameter(String name)
```

#### `getRequestDispatcher(String url)`

**Description:**
The getRequestDispatcher method of the ServletRequest interface is used to obtain a RequestDispatcher for dispatching requests to the specified source. This is usually followed by a `forward(HttpServletRequest request, HttpServletResponse response)` method to forward a request to other resources.

**Usage:**
``` java
request.getRequestDispatcher(String url).forward(HttpServletRequest request, HttpServletResponse response);
```

### Sample Question

> The `ServletResponse` interface in the Java API documentation is defined as an object to assist a servlet in sending a response to the client. Below are three methods of this interface that are commonly used.

#### `setContentType(String type)`

**Description:** The `setContentType` method of the `ServletResponse` interface is used to set the MIME type of the response being sent to the client. This method informs the client about the format of the data in the response body, enabling correct rendering or processing.

**Usage:**
``` java
response.setContentType("text/html;charset=UTF-8");
```

#### `getWriter()`

**Description:** The `getWriter` method of the `ServletResponse` interface is used to retrieve a `PrintWriter` object that can send character text to the client. This is commonly used to output HTML content or other textual data.

**Usage:**
``` java
PrintWriter out = response.getWriter(); out.println("<html><body>Hello, World!</body></html>");
```

#### `sendRedirect(String location)`

**Description:** The `sendRedirect` method of the `ServletResponse` interface instructs the client to redirect to a different URL. This method is used to perform a client-side redirection, and the new URL is sent back to the client in the HTTP response header.

**Usage:**

```java
response.sendRedirect("http://www.example.com/newpage");
```


## 2021

### Question 3(b):

> A web container (also known as a Servlet container) is the component of a web server that interacts with Java servlets. Discuss four key responsibilities of a container.

A web container, also known as a Servlet container, is an essential component in Java web server environments, responsible for managing the lifecycle and interactions of Java Servlets. Here are four key responsibilities of a web container:

#### 1. Lifecycle Management

- **Description**: The web container is responsible for the lifecycle management of servlets. This includes loading and instantiating servlets, initializing them with the `init()` method, handling requests by calling the `service()` method, and finally, removing servlets from service using the `destroy()` method.
- **Details**: This process ensures that servlets are properly managed from the time they are created until the web application is shut down or the servlet is no longer needed.

#### 2. Request and Response Handling

- **Description**: The container handles HTTP requests and responses. It receives HTTP requests from clients, creates appropriate `ServletRequest` and `ServletResponse` objects, and passes them to the relevant servlets for processing.
- **Details**: This involves parsing the HTTP request, creating request and response objects, and managing input and output streams. After the servlet processes the request, the container manages sending the response back to the client.

#### 3. Session Management

- **Description**: Web containers are responsible for session management. This includes creating, maintaining, and destroying HTTP sessions, which are essential for tracking user interactions across multiple requests.
- **Details**: The container provides a way to identify users across multiple requests using mechanisms like cookies or URL rewriting and allows servlets to store and retrieve user-specific data using `HttpSession` objects.

#### 4. Security

- **Description**: Implementing security for web applications is a crucial function of the web container. This includes enforcing access controls, authentication, and ensuring secure communication.
- **Details**: The container manages secure communication protocols like HTTPS, handles user authentication, and controls access to resources based on roles. It also provides features like declarative and programmatic security to define security constraints and manage secure user data handling.
 
-

### Question 4(a):

> Identify one occasion where a Servlet is loaded and two where a Servlet is unloaded.

Servlets, which are a fundamental part of Java web applications, have specific lifecycle events where they are loaded and unloaded. Here’s an overview:

#### Occasion When a Servlet is Loaded

1. **Server Startup or First Request**:
    - **Description**: A servlet is typically loaded when the web server (or servlet container) starts up or when it receives its first request, depending on the servlet's configuration in the web application's deployment descriptor (`web.xml`).
    - **Details**:
        - If the servlet is configured with a `<load-on-startup>` tag in `web.xml`, the servlet container loads and initializes the servlet during server startup. This is used for servlets that require some time to initialize (like loading resources or performing startup tasks) or are essential to the application and should be available immediately upon start.
        - If there is no `<load-on-startup>` configuration, the servlet is loaded and initialized upon receiving its first request.

#### Occasions When a Servlet is Unloaded

1. **Server Shutdown**:
    
    - **Description**: Servlets are unloaded when the servlet container (or web server) is shutting down.
    - **Details**:
        - During server shutdown, the `destroy()` method of each servlet is called by the servlet container. This method is used to release resources, save state, or perform any other cleanup before the servlet is taken out of service.
2. **Application Redeployment**:
    
    - **Description**: Servlets are also unloaded when the web application they belong to is redeployed or undeployed.
    - **Details**:
        - Redeployment might occur during an application update or when configuration changes are made. Just like during server shutdown, the `destroy()` method is called on each servlet, allowing for proper cleanup before the servlet is destroyed.

These load and unload events are part of the servlet lifecycle managed by the servlet container, ensuring that servlets are properly initialized before handling requests and are cleanly shutdown, releasing any resources they hold.

### Question 4(b):

> In your opinion what are four intrinsic functions of a Servlet

Servlets in Java EE play a pivotal role in handling HTTP requests and generating dynamic content. Here are four intrinsic functions of a servlet:

#### 1. Request Processing

- **Description**: The primary function of a servlet is to handle client requests. Upon receiving a request, the servlet processes it based on the logic defined within its `doGet`, `doPost`, and other `doXXX` methods for different HTTP methods.
- **Details**: This involves reading request parameters (`getParameter`), headers (`getHeader`), and body content, and then generating an appropriate response based on this data.

#### 2. Response Generation

- **Description**: Servlets are responsible for generating responses to client requests. This might include outputting HTML, JSON, XML, or other data formats.
- **Details**: Using the `ServletResponse` object, servlets write response content, set content type (`setContentType`), and manage other aspects of the response like setting headers or cookies.

#### 3. Session Management

- **Description**: Servlets handle session management, which is crucial for maintaining state in the stateless HTTP protocol.
- **Details**: Through the `HttpSession` object, servlets can track user sessions across multiple requests, store and retrieve session-scope data, and manage session lifecycle (creation, invalidation).

#### 4. Security Handling

- **Description**: Servlets also contribute to the security aspects of a web application.
- **Details**: They can enforce access controls, authenticate users, and integrate with Java EE security mechanisms to ensure that web application resources are securely managed.

These functions are fundamental to the role of servlets in Java web applications, enabling them to serve as the backbone for processing HTTP requests and generating dynamic, interactive web content.