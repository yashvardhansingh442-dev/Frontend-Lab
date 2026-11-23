# Lesson 1: How the Web Works

## 1.1 Learning objectives
After this lesson, you can:
- Name the parts of a web request.
- Explain the job of a client and a server.
- Explain the parts of a URL.
- Name the roles of HTML, CSS, and JavaScript.

## 1.2 Key terms

| Term | Meaning |
|------|---------|
| Client | A device or program that asks for data. Your browser is a client. |
| Server | A computer that stores files and sends them to clients. |
| Browser | A program that gets web pages and shows them. Examples: Chrome, Firefox, Safari, Edge. |
| HTTP | HyperText Transfer Protocol. The set of rules that a client and a server use to talk. |
| HTTPS | HTTP with encryption. It keeps the data private. |
| URL | Uniform Resource Locator. The address of a resource on the web. |
| DNS | Domain Name System. It changes a domain name into an IP address. |
| IP address | A number that identifies a computer on a network. Example: `93.184.216.34` |
| Request | A message from the client to the server. |
| Response | A message from the server to the client. |

## 1.3 The request and response cycle

Follow these steps when you open `https://example.com` in a browser:

1. **You type the URL.** The browser reads it.
2. **The browser asks DNS for the IP address.** DNS is like a phone book for the web.
3. **The browser opens a connection to the server.** For HTTPS, the browser and server also set up encryption.
4. **The browser sends an HTTP request.** The request says: "Send me the page at `/`."
5. **The server sends an HTTP response.** The response has a status code, headers, and a body. The body is the HTML file.
6. **The browser reads the HTML.** It finds other files that it needs (CSS, JavaScript, images, fonts).
7. **The browser asks for those files.** Steps 4 to 6 repeat for each file.
8. **The browser shows the page.**

```
 Browser (client)                          Server
      |                                       |
      |  1. DNS lookup (name -> IP)           |
      |-------------------------------------->|
      |  2. HTTP request: GET /index.html     |
      |-------------------------------------->|
      |  3. HTTP response: 200 OK + HTML      |
      |<--------------------------------------|
      |  4. Requests for CSS, JS, images      |
      |-------------------------------------->|
      |<--------------------------------------|
      |  5. Browser draws the page            |
```

## 1.4 Parts of a URL

```
https://www.example.com:443/blog/post.html?id=7#comments
\___/   \_____________/ \_/ \____________/ \___/ \______/
  |            |         |        |          |       |
scheme       host      port     path       query  fragment
```

| Part | Example | Meaning |
|------|---------|---------|
| Scheme | `https` | The protocol to use. |
| Host | `www.example.com` | The name of the server. |
| Port | `443` | The door on the server. HTTPS uses 443. HTTP uses 80. The browser hides the default port. |
| Path | `/blog/post.html` | The location of the file on the server. |
| Query | `?id=7` | Extra data that you send to the server. |
| Fragment | `#comments` | A place inside the page. The browser does not send it to the server. |

## 1.5 Common HTTP status codes

| Code | Name | Meaning |
|------|------|---------|
| 200 | OK | The request worked. |
| 301 | Moved Permanently | The page has a new address. |
| 304 | Not Modified | Use the copy that you saved before. |
| 403 | Forbidden | You do not have permission. |
| 404 | Not Found | The server does not have this page. |
| 500 | Internal Server Error | The server has a problem. |

**Memory rule:** 2xx = success. 3xx = redirect. 4xx = client error. 5xx = server error.

## 1.6 The three languages of the web

| Language | Job | Simple example |
|----------|-----|----------------|
| **HTML** | Structure and content | "This is a heading. This is a paragraph." |
| **CSS** | Appearance | "Make the heading blue." |
| **JavaScript** | Behavior | "Show a message when the user clicks." |

Think of a house:
- HTML is the walls and rooms.
- CSS is the paint and furniture.
- JavaScript is the electricity and switches.

This course starts with HTML. HTML is the base for all web pages.

## 1.7 Try It: See a real request

1. Open Chrome or Edge.
2. Go to `https://example.com`.
3. Press `F12` to open Developer Tools.
4. Click the **Network** tab.
5. Press `Ctrl + R` (Windows/Linux) or `Cmd + R` (macOS) to reload.
6. Click the first item in the list (`example.com`).
7. Read the **Headers** tab. Find the status code and the request method.
8. Click the **Response** tab. This is the HTML of the page.

## 1.8 Advanced Note: What the browser does with HTML

The browser does these steps to show a page (the rendering pipeline):

1. **Parse HTML.** The browser builds the **DOM** (Document Object Model), a tree of objects.
2. **Parse CSS.** The browser builds the **CSSOM**.
3. **Combine.** The browser makes the **render tree**. It has only the visible nodes.
4. **Layout.** The browser calculates size and position of each box.
5. **Paint.** The browser draws pixels.
6. **Composite.** The browser puts the layers together on the screen.

More facts for advanced learners:
- The HTML parser works in a stream. It can start to build the DOM before the full file arrives.
- A `<script>` tag without `defer` or `async` blocks the parser. You learn this in Module 10.
- HTTP/2 and HTTP/3 let the browser send many requests on one connection.
- Servers use `Cache-Control` headers to tell the browser how long to keep a file.

## 1.9 Exercises

1. Write the full path of the request cycle in your own words (8 steps maximum).
2. Divide this URL into its parts: `http://shop.test:8080/items/list?sort=price#top`
3. Open any website. In the Network tab, find one 200 response, and one file type that is not HTML.
4. Type a wrong address, such as `https://example.com/nothing-here`. Find the status code.
5. **Advanced:** Find the `Content-Type` and `Cache-Control` headers for the HTML response. Write what each header does.

## 1.10 Check your understanding
- What is the difference between a client and a server?
- What does DNS do?
- Which language gives a page its structure?
- What does a 404 code mean?
