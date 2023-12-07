## 2022

### Question 3(a):

> WebSocket is a leveraged technology of the HTTP protocol. In your answer book, present five differences between web sockets and HTTP. Further to that, identify a scenario where web sockets would be more beneficial than HTTP.

#### Differences Between WebSockets and HTTP

##### 1. Connection Type

- **HTTP**:
    - HTTP is based on a request-response model, which is stateless. Each request from the client is independent and requires its own TCP connection.
- **WebSockets**:
    - WebSockets establish a persistent, full-duplex communication channel over a single long-lived connection. Once established, the WebSocket connection remains open, allowing real-time bidirectional data transfer.

##### 2. Overhead

- **HTTP**:
    - HTTP, especially HTTP/1.1, can have significant overhead due to headers and the need to establish a new TCP connection for each request/response pair (although HTTP/2 has introduced improvements in this area).
- **WebSockets**:
    - WebSockets have a much lower overhead after the initial handshake. They do not require headers to be sent with each message, reducing the amount of redundant data transferred between client and server.

##### 3. Data Transfer Model

- **HTTP**:
    - HTTP is primarily designed for document transfer and operates in a unidirectional manner from client to server (though responses can contain data).
- **WebSockets**:
    - WebSockets support a bidirectional communication model, allowing both the client and server to send data independently and simultaneously.

##### 4. Protocols

- **HTTP**:
    - HTTP is a distinct protocol with its own set of methods (GET, POST, PUT, DELETE, etc.).
- **WebSockets**:
    - WebSocket is a different protocol from HTTP, although it starts as an HTTP handshake. It's designed to work over the same ports as HTTP (80) and HTTPS (443) for compatibility.

##### 5. Use Cases

- **HTTP**:
    - Ideal for transactional requests and responses, where the client initiates the request, and the server responds.
- **WebSockets**:
    - Suited for situations where you need real-time updates from the server, as in chat applications, live feeds, or collaborative editing.

#### Scenario Where WebSockets Would Be More Beneficial Than HTTP

**Real-time Online Multiplayer Games**:

- In online multiplayer games, players need to receive real-time updates about the game state, actions of other players, and in-game events.
- WebSockets allow a continuous, open connection between the client and the server, enabling instant data transfer without the overhead of repeated HTTP requests. This is crucial for maintaining the game's real-time aspect, ensuring low latency and a synchronized state across all clients.
- Using HTTP for this purpose would introduce latency and overhead, making the game experience less responsive and potentially leading to desynchronization issues.

## 2021

### Question 4(e):

> Compare and contrast the use of Web Sockets and HTTP.

Comparing and contrasting WebSockets and HTTP involves understanding their fundamental differences in design, functionality, and suitable use cases. Here's a detailed comparison:

#### Protocol Design

- **WebSockets**:
    
    - WebSocket is a protocol providing full-duplex communication channels over a single TCP connection. It was designed to provide bidirectional, real-time communication between web clients and servers.
    - Initiated with an HTTP handshake (HTTP upgrade request), it then upgrades to a WebSocket connection, allowing continuous data flow without the need to re-establish connections for each data exchange.
- **HTTP**:
    
    - HTTP (HyperText Transfer Protocol) is a request-response protocol in the client-server computing model. It's stateless, meaning each request from a client to server is treated as independent.
    - HTTP/1.1 opens a new TCP connection for each request-response (though it allows for pipelining), and HTTP/2 introduces multiplexing over a single connection but still follows the request-response model.

#### Data Transfer

- **WebSockets**:
    
    - Allows two-way communication where both the client and server can send messages independently once the connection is established.
    - Lower overhead after the initial handshake, making it more efficient for frequent and small messages.
- **HTTP**:
    
    - Primarily unidirectional where the client sends a request, and the server responds. HTTP/2 improves on this but still adheres to the request-response paradigm.
    - Each request may include headers and other metadata, leading to potential overhead, especially in HTTP/1.1.

#### Connection Persistence

- **WebSockets**:
    
    - Creates a persistent connection between the client and server, which remains open until explicitly closed by either the client or server.
    - Suitable for real-time applications where continuous data exchange is required.
- **HTTP**:
    
    - By default, not persistent (though HTTP/1.1 supports keep-alive connections, and HTTP/2 provides persistent streams).
    - Connections typically close after the response is delivered, making it suitable for discrete transactions.

#### Use Cases

- **WebSockets**:
    
    - Ideal for applications requiring real-time updates such as chat applications, live sports updates, online gaming, and collaborative platforms.
    - Beneficial where the overhead of HTTP is a bottleneck, and continuous data flow is needed.
- **HTTP**:
    
    - Used for most web applications, especially those following RESTful principles.
    - Well-suited for document retrieval, form submissions, and other typical web interactions where a continual connection isn't necessary.

#### Scalability

- **WebSockets**:
    
    - While offering real-time capabilities, maintaining a large number of open WebSocket connections can be resource-intensive and challenging to scale.
- **HTTP**:
    
    - Generally more scalable for typical web applications due to its stateless nature. Each request is independent, and resources can be freed immediately after serving a response.

#### Conclusion

- **Complementary Technologies**: While WebSockets and HTTP are designed for different purposes, they are not mutually exclusive and can be used complementarily in the same application.
- **Choice Depends on Requirements**: The choice between WebSockets and HTTP depends on the specific needs of the application, particularly regarding real-time capabilities, data flow patterns, and scalability considerations.