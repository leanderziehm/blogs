# HTTP Headers Security



| Abbreviation | Full                          |
| ------------ | ----------------------------- |
| CSP          | Content Security Policy       |
| CSRF         | Cross-Site Request Forgery    |
| XSS          | Cross-Site Scripting          |
| CORS         | Cross-Origin Resource Sharing |



Strict-Transport-Security:

[https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Strict-Transport-Security](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Strict-Transport-Security)





**Common Security Headers:**

| Header                                      | Purpose                                                                               |
| ------------------------------------------- | ------------------------------------------------------------------------------------- |
| `Content-Security-Policy` (CSP)             | Restricts resources (scripts, styles) the browser can load to prevent XSS.            |
| `Strict-Transport-Security` (HSTS)          | Forces browsers to use HTTPS for all future requests.                                 |
| `X-Content-Type-Options`                    | Prevents MIME type sniffing to avoid content-based attacks.                           |
| `X-Frame-Options`                           | Prevents clickjacking by restricting embedding of the page in frames.                 |
| `Referrer-Policy`                           | Controls what referrer information is sent to other sites.                            |
| `Permissions-Policy`                        | Restricts browser features like geolocation or camera access.                         |
| `Set-Cookie` (with `Secure` and `HttpOnly`) | Protects cookies from being sent over insecure connections or accessed by JavaScript. |



### 1. **Content Security Policy (CSP)**

**Header:** `Content-Security-Policy`

**Purpose:** Prevents cross-site scripting (XSS), clickjacking, and data injection attacks by controlling sources of content that the browser can load.

**Example:**

```
Content-Security-Policy: default-src 'self'; img-src https://images.example.com; script-src 'self' 'unsafe-inline'
```

**Notes:**

* Defines allowed sources for scripts, images, styles, frames, etc.
* `'self'` allows content from the same origin.
* `'unsafe-inline'` should generally be avoided; it weakens protection.

***

### 2. **Strict-Transport-Security (HSTS)**

**Header:** `Strict-Transport-Security`

**Purpose:** Forces the browser to communicate only over HTTPS, preventing downgrade attacks.

**Example:**

```
Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
```

**Notes:**

* `max-age` is in seconds (1 year = 31,536,000 seconds).
* `includeSubDomains` applies HSTS to all subdomains.
* `preload` allows inclusion in browser preload lists for HTTPS enforcement.

***

### 3. **X-Content-Type-Options**

**Header:** `X-Content-Type-Options: nosniff`

**Purpose:** Prevents browsers from MIME-sniffing files, forcing them to follow the declared `Content-Type`. Reduces risk of XSS via incorrect content interpretation.

***

### 4. **X-Frame-Options**

**Header:** `X-Frame-Options`

**Purpose:** Prevents clickjacking by controlling whether the page can be framed.

**Values:**

* `DENY` – Disallows any framing.
* `SAMEORIGIN` – Allows framing only from the same origin.
* `ALLOW-FROM uri` – Allows framing from specific URI (deprecated in some browsers).

**Example:**

```
X-Frame-Options: SAMEORIGIN
```

***

### 5. **X-XSS-Protection**

**Header:** `X-XSS-Protection`

**Purpose:** Enables browser XSS filtering. Mostly deprecated, modern browsers rely on CSP instead.

**Example:**

```
X-XSS-Protection: 1; mode=block
```

***

### 6. **Referrer-Policy**

**Header:** `Referrer-Policy`

**Purpose:** Controls how much referrer information is sent in requests.

**Common Values:**

* `no-referrer` – Never sends the referrer.
* `same-origin` – Only sends referrer to the same origin.
* `strict-origin-when-cross-origin` – Default in modern browsers, sends minimal info cross-origin.

***

### 7. **Permissions-Policy (formerly Feature-Policy)**

**Header:** `Permissions-Policy`

**Purpose:** Controls which browser features (camera, microphone, geolocation) can be used by the site or embedded content.

**Example:**

```
Permissions-Policy: geolocation=(self), camera=()
```

***

### 8. **Set-Cookie Security Flags**

When setting cookies, headers can include:

* `Secure` – Cookie sent only over HTTPS.
* `HttpOnly` – Cookie inaccessible via JavaScript.
* `SameSite=Strict|Lax|None` – Controls cross-site cookie sending to prevent CSRF.

**Example:**

```
Set-Cookie: sessionId=abc123; Secure; HttpOnly; SameSite=Strict
```

***

### Best Practices

1. Always serve your site over HTTPS and enable HSTS.
2. Use a strict CSP to prevent XSS attacks.
3. Avoid unnecessary exposure of referrer information.
4. Protect framing to prevent clickjacking.
5. Use secure cookie attributes to mitigate CSRF and session hijacking.
6. Regularly review security headers with tools like [SecurityHeaders.io](https://securityheaders.io/).



Good Videos:

{% embed url="https://www.youtube.com/watch?v=-LjPRzFR5f0" %}



{% embed url="https://www.youtube.com/watch?v=064yDG7Rz80" %}





I still need to Watch:

{% embed url="https://www.youtube.com/watch?v=xbPK6ux9C7o&pp=0gcJCcUKAYcqIYzv" %}

{% embed url="https://www.youtube.com/watch?v=eFbFMqaqSAk" %}

{% embed url="https://www.youtube.com/watch?v=LBIANHdBoUA" %}

{% embed url="https://www.youtube.com/watch?v=mr230uotw-Y" %}

{% embed url="https://www.youtube.com/watch?v=seAb9Q3OqK8" %}
