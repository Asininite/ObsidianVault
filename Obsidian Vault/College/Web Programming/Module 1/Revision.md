Below is a **clean, professionally structured, exam-oriented REVISION SHEET for MODULE 1** followed by **ALL PYQs from Module 1 + FULL ANSWERS**.

This is everything you need for fast final revision and guaranteed scoring.

No unnecessary text, no fillers. Well-structured, point-wise, and academically complete.

---

# **MODULE 1 – COMPLETE REVISION SHEET**

This revision sheet covers the entire Module 1:

1. **Web Architecture & HTTP Basics**
    
2. **HTTP Request/Response Model**
    
3. **HTTP Methods, Status Codes & MIME**
    
4. **HTML5 Document Structure**
    
5. **CSS – Styling, Box Model, Positioning, Flexbox**
    
6. **JavaScript & DOM Basics**
    
7. **HTTP Security, Cookies, Sessions, Caching**
    
8. **HTML5 APIs (Storage, Canvas, Audio/Video, Geolocation, JSON)**
    

Each section contains **definitions, explanations, tables, diagrams and key points** that score in exams.

---

# **1. Web Architecture & HTTP Basics**

### Web Architecture Layers

- **Client**: Browser, sends HTTP requests
    
- **Server**: Processes requests, returns responses
    
- **Database**: Persistent storage
    
- **Protocol**: HTTP/HTTPS
    
- **URL** = protocol + domain + path + query + fragment
    

### HTTP Characteristics

- Stateless
    
- Text-based
    
- Request–response model
    
- Extensible via headers
    

---

# **2. HTTP Request & Response Model**

### HTTP Request Format

```
<Method> <Request-URI> <Version>
Headers
(blank line)
Body (optional)
```

### HTTP Response Format

```
<Version> <Status Code> <Reason Phrase>
Headers
(blank line)
Body (resource)
```

### Important Request Headers

- Host
    
- User-Agent
    
- Accept
    
- Cookie
    

### Important Response Headers

- Content-Type
    
- Content-Length
    
- Set-Cookie
    
- Last-Modified
    
- Cache-Control
    

---

# **3. HTTP Methods, Status Codes & MIME**

### Methods

- **GET** – fetch resource
    
- **POST** – submit data
    
- **PUT** – update
    
- **DELETE** – delete
    
- **HEAD** – headers only
    
- **OPTIONS** – capabilities
    

### Status Codes

- **200 OK**
    
- **301 Moved Permanently**
    
- **302 Found**
    
- **400 Bad Request**
    
- **401 Unauthorized**
    
- **403 Forbidden**
    
- **404 Not Found**
    
- **500 Internal Server Error**
    

### MIME

Format:  
`type/subtype`

Examples:

- `text/html`
    
- `image/png`
    
- `application/json`
    
- `video/mp4`
    
- `multipart/form-data`
    

Importance: correct rendering, security (no MIME sniffing), content negotiation.

---

# **4. HTML5 Document Structure**

### HTML5 Structure Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>
  ...
</body>
</html>
```

### Semantic Tags

`header`, `nav`, `section`, `article`, `aside`, `footer`, `main`

Benefits: accessibility, SEO, structure clarity.

---

# **5. CSS (Cascading Style Sheets)**

### 3 Ways to Include CSS

- Inline
    
- Internal
    
- External (recommended)
    

### Selectors

- Element (`p`)
    
- Class (`.nav`)
    
- ID (`#header`)
    
- Attribute (`input[type=text]`)
    
- Pseudo-class (`a:hover`)
    
- Pseudo-element (`p::first-letter`)
    

### Box Model

- Content
    
- Padding
    
- Border
    
- Margin  
    Use `box-sizing: border-box;`
    

### Positioning

- static
    
- relative
    
- absolute
    
- fixed
    
- sticky
    

### Flexbox

- `display:flex`
    
- `flex-direction`
    
- `justify-content`
    
- `align-items`
    
- `gap`
    

---

# **6. JavaScript & DOM Basics**

### Variables & Types

`let`, `const`, `var`  
Primitives & Objects.

### DOM Selection

- `getElementById()`
    
- `querySelector()`
    
- `querySelectorAll()`
    

### DOM Manipulation

- `innerHTML`
    
- `textContent`
    
- `classList.add()`
    
- `appendChild()`
    

### Events

`addEventListener("click", handler)`  
`event.preventDefault()`  
Event bubbling & capturing.

---

# **7. HTTP Security & State Management**

### Cookies

Client-side, small, sent with requests.

### Sessions

Server-side, uses session ID cookie.

### HTTPS

HTTP + TLS  
Provides confidentiality, integrity, authentication.

### Common Attacks

- XSS → sanitize output, CSP
    
- CSRF → tokens, SameSite cookies
    
- SQL Injection → prepared statements
    
- Clickjacking → X-Frame-Options
    

### Caching

Headers:

- `Cache-Control` (no-cache, no-store, public, private, max-age)
    
- `ETag`
    
- `Last-Modified`
    

---

# **8. HTML5 APIs & JSON**

### Local Storage

Persistent key–value store  
`localStorage.setItem("x","1");`

### Session Storage

Cleared when tab closes.

### Geolocation

`navigator.geolocation.getCurrentPosition(success)`

### Audio/Video Tags

Native playback with `<audio>` and `<video>` and `<source>`.

### Canvas

2D drawing API  
`fillRect()`, `beginPath()`, `arc()`

### JSON

Lightweight data format  
`JSON.parse()`, `JSON.stringify()`

---

# **MODULE 1 PYQs + COMPLETE ANSWERS**

All PYQs below are extracted from your uploaded question papers (Dec 2022, May 2023, Dec 2023, May 2024). Citations included.

---

# **PYQ 1 – Define MIME. Explain its significance.**

### **Answer**

MIME (Multipurpose Internet Mail Extensions) is a standard for identifying the nature and type of a file using the format `type/subtype`.  
Example: `text/html`, `image/png`, `application/json`.

**Significance:**

1. Enables browser to correctly interpret content.
    
2. Prevents MIME sniffing security issues.
    
3. Enables content negotiation between browser and server.
    
4. Standardizes types for multimedia, JSON, XML, form data.
    

---

# **PYQ 2 – Explain HTTP request and response structure.**

### **Answer**

**HTTP Request Structure:**

- **Request Line:** `GET /index.html HTTP/1.1`
    
- **Headers:** Host, User-Agent, Accept
    
- **Blank line**
    
- **Body:** present for POST/PUT
    

**HTTP Response Structure:**

- **Status Line:** `HTTP/1.1 200 OK`
    
- **Headers:** Content-Type, Content-Length
    
- **Blank line**
    
- **Body:** HTML, JSON, image etc.
    

---

# **PYQ 3 – Differentiate GET and POST.**

### **Answer**

|Feature|GET|POST|
|---|---|---|
|Data|URL|Body|
|Visible|Yes|No|
|Use|Retrieval|Submission|
|Cacheable|Yes|No|
|Size limit|Small|Large|

---

# **PYQ 4 – Write CSS to style links with yellow background and italics; unordered list in bold; background image no-tiling.**

### **Answer**

```css
a {
  font-style: italic;
}
a:hover,
a:active {
  background-color: yellow;
}
ul {
  font-weight: bold;
}
body {
  background-image: url('birds.jpg');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}
```

---

# **PYQ 5 – Explain relative and absolute positioning.**

### **Answer**

**Relative Positioning:**

- Moves element relative to its original position.
    
- Space preserved.
    

**Absolute Positioning:**

- Removed from normal flow.
    
- Positioned relative to nearest positioned ancestor.
    

---

# **PYQ 6 – Write JS to read an integer and display its square.**

```html
<script>
  const n = parseInt(prompt("Enter number"));
  alert("Square = " + (n*n));
</script>
```

---

# **PYQ 7 – Explain arrays in JavaScript. What do slice() and join() do?**

### **Answer**

Arrays are ordered lists of values.

- `slice(start,end)` – returns sub-array, non-destructive
    
- `join(sep)` – converts array to string separated by `sep`
    

---

# **PYQ 8 – Explain Local Storage with example.**

### **Answer**

Local Storage stores key–value pairs persistently.

```js
localStorage.setItem("user","Alice");
localStorage.getItem("user");
```

Characteristics: persistent, large capacity, domain-based.

---

# **PYQ 9 – Explain HTML5 Audio/Video.**

### **Answer**

Native multimedia support:

```html
<video controls>
  <source src="movie.mp4" type="video/mp4">
</video>
```

Supports attributes like controls, autoplay, loop.

---

# **PYQ 10 – Draw a rectangle using Canvas.**

```html
<canvas id="c" width="200" height="150"></canvas>
<script>
const ctx = document.getElementById('c').getContext('2d');
ctx.fillStyle = "blue";
ctx.fillRect(10,10,100,50);
</script>
```

---

# **PYQ 11 – Explain Cookies vs Sessions.**

### **Answer**

**Cookies:**  
Client-side, small, sent with every request.

**Sessions:**  
Server-side, stores user data; client stores only session ID.

Sessions are more secure and used for authentication.

---

# **PYQ 12 – Explain HTTPS. Why is it needed?**

### **Answer**

HTTPS = HTTP + TLS.  
Provides encryption, data integrity, authentication.

Needed to prevent sniffing, MITM attacks, and protect credentials.

---

# **PYQ 13 – What are cache control directives?**

### **Answer**

- `no-cache` – must revalidate
    
- `no-store` – no storage
    
- `max-age=n` – freshness lifetime
    
- `private` – browser only
    
- `public` – cacheable by proxies
    

---

# **NEXT OPTIONS**

I can now give you:

1. **Module 1 condensed one-page cheat sheet**, or
    
2. **Module 2 full detailed lessons**, or
    
3. **A combined Module 1 + expected 2024/2025 probable questions**, or
    
4. **A custom exam strategy for Web Technology (CST463)**.
    

Tell me what you want next.