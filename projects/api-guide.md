# API Basics

[Home](../index.md) | [API Basics](api-guide.md) | [Software Manual](software-manual.md) | [FAQ](faq.md)

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

## Using an API in a Website

To bring an API into your website, you'll need JavaScript (or a framework) to send a request and display the data in your HTML.

### Example: Displaying Quote of the Day

We'll use API Ninjas' '[Quotes API](https://api-ninjas.com/api/quotes)'

### HTML
Create a basic container that links to jQuery and includes your script:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Random Quote of the Day</title>
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
</head>
<body>
  <h1>Random Quote</h1>
  <blockquote id="quote"></blockquote>
  <cite id="author"></cite>

  <script src="script.js"></script>
</body>
</html>
```

### JavaScript
Add the following code to a file named script.js in the same folder:

```JavaScript
function fetchQuote() {
  $.ajax({
    method: 'GET',
    url: 'https://api.api-ninjas.com/v1/quotes',
    headers: {
      'X-Api-Key': 'YOUR_API_KEY_HERE'
    },
    contentType: 'application/json',
    success: function(result) {
      document.getElementById("quote").textContent = `"${result[0].quote}"`;
      document.getElementById("author").textContent = `— ${result[0].author}`;
    },
    error: function(jqXHR) {
      document.getElementById("quote").textContent = "Failed to load quote.";
      document.getElementById("author").textContent = "";
      console.error("Error:", jqXHR.responseText);
    }
  });
}

fetchQuote();
```
**DEMO** 

<iframe src="https://farringtonwrites.github.io/farrington-portfolio/projects/quote-demo.html"
        width="100%" height="400"
        style="border: none; border-radius: 8px; box-shadow: 0 0 10px rgba(0,0,0,0.1);">
</iframe>

## API Keys
If you look closely at our example, you’ll notice that we had to include a special line in our JavaScript:

```JavaScript
headers: { 'X-Api-Key': 'YOUR_API_KEY_HERE' }
```
This is an API key — a unique identifier that tells the API who you are.

### Why Do APIs Require Keys?
1. **Usage Tracking:** They allow the provider to track requests.
2. **Rate Limiting:** They can prevent abuse by limiting number of requests per user.
3. **Monetization:** The key can be used to grant access to premium/paid subscription levels.
> Requiring a key is not universal. Some open or public APIs (like quotable.io) allow limited use without a key. 


