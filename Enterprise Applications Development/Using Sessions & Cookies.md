## 2021

### Question 1(c):

> *“Using cookies for session tracking is bad practice”*. Defend or refute this statement

**Here are key points in defense of this statement:**

#### 1. Security Vulnerabilities

- **Session Hijacking**: Cookies, especially when not secured properly, can be intercepted by attackers. If session cookies are captured, attackers can impersonate legitimate users, gaining unauthorized access to sensitive information.
- **Cross-Site Scripting (XSS) Attacks**: Non-HTTPOnly cookies are accessible via JavaScript, making them vulnerable to XSS attacks. An attacker can inject malicious scripts to steal cookie data.
- **Cross-Site Request Forgery (CSRF)**: If cookies are used for authentication without additional CSRF protection, attackers can trick users into executing unwanted actions on a web application in which they're authenticated.

#### 2. Privacy Concerns

- **Tracking and Privacy**: Cookies can be used to track user activities across different websites, raising serious privacy concerns. This is particularly problematic with third-party cookies.
- **User Consent and Regulation**: With the growing emphasis on privacy regulations like GDPR, the use of cookies requires explicit user consent. Managing this consent can be challenging and failing to comply with regulations can lead to legal issues.

#### 3. Client-Side Dependence

- **Browser Settings and Limitations**: Users can disable cookies in their browser settings, which can break the session management in applications that rely solely on cookies. Moreover, different browsers have varying limitations on cookie size and quantity, which can affect the application's functionality.
- **Storage Capacity**: Cookies have a limited storage capacity (generally about 4KB per cookie), which is insufficient for storing large amounts of data.

#### 4. Scalability and Performance

- **Load Balancing Issues**: In a distributed server environment, using cookies for session management can be challenging. Load balancers need to implement sticky sessions to ensure requests from the same user session are directed to the same server, which can complicate scalability and fault tolerance.
- **Network Overhead**: Each HTTP request includes cookies in the header, increasing the amount of data transferred between client and server, which can impact performance, especially for applications with frequent server interactions.

#### 5. Modern Alternatives

- **Availability of Better Alternatives**: Modern session management techniques, such as token-based authentication (e.g., JWT), offer more secure and flexible approaches to managing user sessions. These methods often provide enhanced security features and are less reliant on the client’s browser settings.

In conclusion, while cookies have been a standard tool for session tracking, they come with significant security, privacy, and scalability challenges that can make them a less favorable option in certain contexts, particularly in applications requiring robust security and privacy compliance.