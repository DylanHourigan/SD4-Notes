## 2022

### Question 1(c):

> SSL/TSL (Secure Sockets Layer/Transport Layer Security) protects data in transit between a browser and a server. Describe in detail how it works.

SSL/TLS (Secure Sockets Layer/Transport Layer Security) is a protocol designed to secure communications over computer networks. It's widely used on the internet, particularly for securing data transmitted between web browsers and servers. Here's a detailed explanation of how SSL/TLS works:

#### 1. Establishing a Secure Connection: The SSL/TLS Handshake

- **Initial Contact**: When a client, such as a web browser, attempts to establish a secure connection to a server, it starts by sending a "ClientHello" message. This message includes the SSL/TLS version the client supports, a list of supported cryptographic algorithms (ciphers), and a random byte string for session security.
    
- **Server Response**: The server replies with a "ServerHello" message, selecting the SSL/TLS version and a cipher from the client’s list. The server also sends its digital certificate, which contains the server's public key and is issued by a trusted Certificate Authority (CA).
    
- **Certificate Verification**: The client verifies the server’s certificate against a list of trusted CAs. If the certificate is valid, the client trusts the server's public key.
    
- **Key Exchange**: The client then uses the server's public key to encrypt a random byte string and sends it to the server. This string is used to generate a symmetric session key.
    
- **Secure Symmetric Encryption**: Both client and server use the symmetric session key for encrypting and decrypting the data they send to each other. This key is unique to the session, ensuring secure communication.
    

#### 2. Data Transfer

- **Encryption**: Once the secure connection is established, the client and server can start exchanging data. All transmitted data is encrypted with the session key.
    
- **Data Integrity**: SSL/TLS also ensures the integrity of the data. Each message contains a message authentication code (MAC) to verify the data hasn’t been altered.
    

#### 3. Closing the Session

- Either the client or server can choose to end the session. When this happens, a "close_notify" alert is sent, and the session key is discarded.

#### Additional Key Points


- **Role of Cryptography**: SSL/TLS uses a combination of asymmetric and symmetric cryptography. Asymmetric cryptography (via public and private keys) is used during the handshake to securely establish the symmetric key. Symmetric cryptography is then used for the efficient encryption of data during the session.
    
- **Certificates and Trust**: The use of certificates issued by trusted CAs is crucial. It helps prevent man-in-the-middle attacks, where an attacker could impersonate the server.
