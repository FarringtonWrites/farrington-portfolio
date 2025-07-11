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

## Example: Using an API in a Website

To bring an API into your website, you'll need JavaScript (or a framework) to send a request and display the data in your HTML.

### Example 1: Displaying Quote of the Day

We'll use Luke Peavey's 'Quotable API' [Quotable API](https://github.com/lukePeavey/quotable)

### HTML

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Random Quote of the Day</title>
  </head>
  <body>
    <h1>Random Quote</h1>
    <blockquote id="quote"></blockquote>
    <cite id="authot"></cite>

    <script src="script.js"></script>
  </body>
</html>
```

# JavaScript
```JavaScript
fetch("https://api.quotable.io/random?tags=literature")
  .then(response => response.json())
  .then(data => {
    document.getElementById("quote").innerText = `"${data.content}"`;
    document.getElementById("author").innerText = `— ${data.author}`;
  })
  .catch(error => console.error("Error fetching quote:", error));
```
