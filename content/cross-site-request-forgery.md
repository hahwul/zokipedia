+++
title = "Cross-site Request Forgery"
date = 2025-11-01
updated = 2025-11-01
description = "Cross-site request forgery (CSRF) is a type of malicious exploit of a website where unauthorized commands are submitted from a user that the web application trusts."
tags = ["security", "web", "csrf", "attack"]
+++

Cross-site request forgery, also known as one-click attack or session riding and abbreviated as CSRF (sometimes pronounced sea-surf) or XSRF, is a type of malicious exploit of a website or web application where unauthorized commands are submitted from a user that the web application trusts.

## Characteristics

There are many ways in which a malicious website can transmit such commands; for example, specially-crafted image tags using GET requests, hidden forms using POST requests, or JavaScript using XMLHttpRequest.

Unlike cross-site scripting (XSS), which exploits the trust a user has for a particular site, CSRF exploits the trust that a site has in a user's browser.

## History

The term "cross-site request forgery" was coined by Peter Watkins in a June 2001 Bugtraq post about the technique. The attack has been known by several other names, including:

- Session riding
- Cross-site reference forgery
- Hostile linking
- One-click attack
- Automatic form submission attack

## CSRF Attacks in μTorrent WebUI

In 2008, researchers demonstrated CSRF vulnerabilities in μTorrent's web interface. The attack allowed malicious websites to add torrents to a user's download queue without their knowledge.

### Forging login requests

CSRF can also be used to forge login requests. If a site uses only username and password authentication, an attacker can forge a login request and potentially gain access to the user's account.

## HTTP verbs and CSRF

The HTTP GET method is particularly susceptible to CSRF attacks because:

1. GET requests can be triggered by simple image tags
2. GET requests are often cached by browsers and proxies
3. GET requests appear in server logs and referrer headers

### Other approaches to CSRF

- **POST-based CSRF**: Using hidden forms that automatically submit
- **JSON-based CSRF**: Exploiting sites that accept JSON data
- **Flash-based CSRF**: Using Adobe Flash to send cross-domain requests

### Effects

The impact of CSRF attacks can include:

- Unauthorized fund transfers
- Account takeovers
- Data modification or deletion
- Privilege escalation

## Cross-Site Request Forgery

CSRF attacks work by including a link or script in a page that accesses a site to which the user is known (or is supposed) to have authenticated.

### Limitations

CSRF attacks have several limitations:

- The attacker must target either a site that doesn't check the referrer header or a victim with a browser or plugin bug
- The attacker must find a form submission URL
- The attacker must determine the correct values for all the form inputs

## Prevention

### Synchronizer token pattern

The most common method to prevent CSRF attacks is to use a synchronizer token:

```html
<input type="hidden" name="csrf_token" value="abc123def456ghi789">
```

### Cookie-to-header token

Another approach is to use a cookie-to-header token:

1. Send a random value in both a cookie and a custom HTTP header
2. The server verifies that both values match
3. Since cross-site requests cannot read cookies, they cannot set the custom header

### Double Submit Cookie

The double submit cookie technique:

1. Send a random value in a cookie
2. Require the same value to be sent in a form field or header
3. Verify both values match on the server

### SameSite cookie attribute

Modern browsers support the SameSite cookie attribute:

```http
Set-Cookie: sessionid=abc123; SameSite=Strict
```

- `Strict`: Cookie is only sent with same-site requests
- `Lax`: Cookie is sent with same-site requests and top-level navigation
- `None`: Cookie is sent with all requests (requires Secure flag)

### Client-side safeguards

Client-side protection methods include:

- Checking the Origin header
- Implementing custom headers for AJAX requests
- Using CAPTCHA for sensitive operations

### Other techniques

Additional CSRF prevention techniques:

- **Re-authentication**: Require password confirmation for sensitive actions
- **Transaction signing**: Use cryptographic signatures for critical operations
- **User interaction based protection**: Require explicit user actions like clicking buttons

## References

1. Watkins, Peter (2001). "Cross-Site Request Forgeries". Bugtraq.
2. OWASP Foundation. "Cross-Site Request Forgery (CSRF) Prevention Cheat Sheet".
3. Barth, Adam; Jackson, Collin; Mitchell, John C. (2008). "Robust defenses for cross-site request forgery".
4. Zeller, William; Felten, Edward W. (2008). "Cross-site request forgeries: exploitation and prevention".
