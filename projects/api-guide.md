# API Basics

## What is an API?

**API** stands for *Application Programming Interface*. They allow different software applications to communicate and provide access to information without requiring knowledge of the software’s inner workings.

---

## Common API Types

- **REST (Representation State Transfer:** The most common web API style. It uses standard HTTP methods like `GET`, `POST`, `PUT`, and `DELETE`.
- **SOAP (Simple Object Access Protocol):** An older protocol that uses XML and has more rigid standards.
- **GraphQL:** A newer query language for APIs that lets clients request only the data they need.

## Choosing the Right API Type
Different APIs are suited for different cases:
| API TYPE | BEST FOR | PROS | CONS |
|----------|----------|------|------|
| **REST** |General-purpose web services | Simple, widely used, easy to cache | Can be over-fetching or under-fetching data |
| **GraphQL**| Front-end-heavy applications with flexible data needs | Clients choose exact data shape | More complex setup and tooling |
| **SOAP**   | Enterprise-level applications (banking, healthcare) | Strong standards, built-in security | Verbose, less flexible, XML-only |
| **gRPC**   | High-performance microservices | Fast, supports streaming, uses Protobuf | Not human-readable, harder to test/debug |
| **WebSockets** | Real-time apps (chat, live data feeds) | Bi-directional communication | More complex state management |

> In general:  
> - Use **REST** if you're building a typical web app and want simplicity.  
> - Use **GraphQL** if clients need to control the shape of the data.  
> - Use **SOAP** only if working with legacy or enterprise systems that require it.  
> - Use **gRPC** or **WebSockets** for high-performance, low-latency needs.
