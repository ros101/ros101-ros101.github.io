---
layout: notes
---
# Cross Site Request Forgery (CSRF)

A Cross-Site Forgery Attack forces the user to submit data to another website's secure area where he has an active session. The user visits a malicious website and clicks on a link or a button. This action sends an HTTP action directed to another website to trigger an event on behalf of the user. Depending on the design of the targetted website, the HTTP action can be a form, a simple HTTP GET, or a REST call.

<img src="01-csrf-attack.png" alt="Diagram describing a CSRF attack" class="img-responsive"/>

Mitigating this kind of attack is usually quite simple. The server must generate a unique token that the client must include in the subsequent request. The server must generate a new token at every exchange. This practice ensures that every client submission corresponds to an initial interaction initiated by the client.

<img src="02-csrf-prevention.png" alt="Diagram showing CSRF attack and mitigation" class="img-responsive"/>

The same-origin policy active in all modern browsers protects the user from this attack when using REST APIs (unless the server explicitly disables it with the CORS header). HTTP GET should never change the server's state and be a possible target. This leaves HTML Forms as the only risk. Many web frameworks can generate safe forms without requiring manual coding. They include the CSRF token as a hidden field and automatically check the token in the submitted data.

[diagrams](csrf-attack-prevention.drawio) editable on [app.diagrams.net](https://app.diagrams.net)

## Reference

OWASP (N.A.) Cross Site Request Forgery (CSRF). Available from: https://owasp.org/www-community/attacks/csrf [Accessed on 8/03/2022]

---

## Reply to a comment

> If the unique token is passed as part of the HTML form in the request, isn't there a danger that it can be intercepted. You state that the token is 'hidden' on the form. Do you know how this is achieved?

With "hidden field", I mean an input tag with the attribute "type" equal to "hidden" which means that it should not be displayed on the screen. Sorry if it was not very clear.

For example, imagine the form of an internet banking website:

```html
<form action="/payment">
  <label for="iban">IBAN:</label>
  <input type="text" id="iban" name="iban"/><br/>
  <label for="amount">Amount:</label>
  <input type="text" id="amount" name="amount"/><br/>
  <input type="hidden" id="token" name="token" value="c319927fd5898ac">
  <input type="submit" value="Submit">
</form>
```

The token must change every time, and it cannot be predicted.

To scam a user, the attacker should:

* wait until the user tries to perform a payment.
* intercept the token (e.g. with a man-in-the-middle).
* lure the user to his malicious website and convince him to click on something.
* everything must happen while the session is still alive and before the user submits the original form or change page on the internet banking (it would burn the token).

Even if the attacker intercepts the token, it is useless unless the user performs those specific actions.

The bank should also use additional strategies to avoid interception (like encryption).
