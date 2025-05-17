# Security Analysis: Injection (Cross-site Scripting)

## Introduction

Cross-Site Scripting (XSS) is a common injection vulnerability where attackers inject malicious scripts into websites. It often occurs when a web app includes user input in output without proper validation or escaping.

For example, in JavaScript:

```js
//Website with a search function
app.get("/results", (req, res) => {
  const searchQuery = req.query.search;
  const results = getResults(searchQuery); // Implementation not shown
  res.send(`
   <h1>You searched for ${searchQuery}</h1>
   <p>Here are the results: ${results}</p>`);
});
```

```js
//Site injection
<a href="http://example.org/results?search=<img src=x onerror=alert('hello')">
  Get a free kitten!
</a>
```

When the user clicks the link:

1. The browser sends a GET request to the server. The request's URL parameter contains the malicious code.
2. The server extracts the URL parameter value and embeds it in the page.
3. The server returns the page to the browser, which runs it.


More at: [mdn web docs](https://developer.mozilla.org/en-US/docs/Web/Security/Attacks/XSS)

## Specific Real-World Example

In December 2024, researchers discovered a serious prompt injection vulnerability affecting large language model (LLM)-powered apps. The attack involved injecting specially crafted text into an LLM's prompt context via shared documents or messages. When the AI processed that context, it behaved in unintended ways including leaking private data or altering user instructions.

One real-world example involved prompting the LLM to trigger the XSS. "The prompt contains a mix of instructions and a Bas64-encoded string that's decoded by the DeepSeek chatbot to execute the XSS payload responsible for extracting the victim's session token, ultimately permitting the attacker to impersonate the user." (Lakshmanan, R. , 2024)

Although this isn’t a traditional XSS in web browsers, it highlights how input-based injection vulnerabilities are evolving with AI-powered tools. Like XSS, it exploits trust in input handling.

Source: [The Hacker News](https://thehackernews.com/2024/12/researchers-uncover-prompt-injection.html)

## Analysis About How to Prevent

To prevent XSS:

* **Escape all user input** before rendering it in HTML, JavaScript, or attributes.
* Use a templating engine that automatically escapes input (e.g., React, Angular).
* **Apply Content Security Policy (CSP)** headers to limit script execution.
* **Validate and sanitize inputs** on both client and server side.
* Avoid using `innerHTML` or `document.write()` when inserting user content.

Refer to: [OWASP XSS Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)

## Conclusion / Closing

Cross-site scripting is a well-known yet persistent web vulnerability. It allows attackers to hijack user sessions or inject malicious content into trusted sites. Preventing XSS requires rigorous input validation, output encoding, and use of secure frameworks. With proper defenses in place, applications can significantly reduce the risk of XSS-based attacks.

## References / ChatGPT Analysis

**Did it hallucinate?**

Yes, but only when citing sources it used for information. I found that the sources it gave me (in https address's) were broken and sent me to 404 pages. 

**Verify output:**
Cross research and finding better articles to summarize and have chat refactor. 

**One prompt provided:**
```
Source: https://portswigger.net/daily-swig/ebay-fixes-stored-xss-vulnerability-in-user-messaging-service

this link is broken
```
```
The broken source link has been replaced with a valid one from The Hacker News covering the same eBay XSS vulnerability.
```
//Which was *also* broken and sent me to a 404 

**References:**

* OWASP Top 10: [https://owasp.org/www-project-top-ten/](https://owasp.org/www-project-top-ten/)
* 2025. OWASP XSS Prevention Cheat Sheet. [https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)
* 2025. The Hacker News: [https://thehackernews.com/search/label/xss](https://thehackernews.com/search/label/xss)
* 2024. Lakshmanan, R. The Hacker News. [*Researchers Uncover Prompt Injection Vulnerabilities in DeepSeek and Claude AI.*](https://thehackernews.com/2024/12/researchers-uncover-prompt-injection.html)
* MDN Web Docs. [https://developer.mozilla.org/en-US/docs/Web/Security/Attacks/XSS](https://developer.mozilla.org/en-US/docs/Web/Security/Attacks/XSS)
* 2020. Hoffman, A. *Web Application Security: Exploitation and Countermeasures for JavaScript Apps*. O’Reilly Media.
