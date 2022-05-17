---
layout: notes
---
# Discussion 1: Cross Site Request Forgery - summary

Follow-up of [Unit 1](../unit1) and [Unit 2](../unit2/csrf-attack) discussions

A Cross-Site Forgery Attack forces the user to submit data to another website's secure area where he has an active session. The user visits a malicious website and clicks on a link or a button. This action sends an HTTP action directed to another website to trigger an event on behalf of the user. Depending on the design of the targeted website, the HTTP action can be a form, a simple HTTP GET, or a REST call.

<img src="01-csrf-attack.png" alt="Diagram describing a CSRF attack" class="img-responsive"/>

To mitigate the attack, the client and server must share a server-generated token that changes at every request to ensure that every client submission corresponds to an initial interaction initiated by the client.

<img src="02-csrf-prevention.png" alt="Diagram showing CSRF attack and mitigation" class="img-responsive"/>

The same-origin policy by default protects the user when using REST APIs. This leaves HTML Forms as the only risk. Many web frameworks include the token as a hidden input field and automatically perform its validation. The token could be exposed to the user without compromising security as long as the attacker is unable to discover it.

The following is a simplified example for an internet banking website:

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

An effective attack should mix other techniques.

With a Man in the Middle, the attacker would be able to intercept the token (as well as a 2FA). In this scenario, there is no need for social engineering or malicious websites: the attacker could simply intercept the form and submit it directly.

<img src="csrf-attack-1.png" alt="MITM attack" class="img-responsive"/>

In a different scenario, a malicious browser extension could manipulate the page and induce the user in error.

<img src="csrf-attack-2.png" alt="browser attack" class="img-responsive"/>

In conclusion, if the attacker is able to intercept the data, he needs minimal or even no cooperation from the user. It should also be considered, however, that the steps to perform a Man in the Middle require a lot of control over the victim's network and system when encryption is in place.


## Reference

OWASP (N.A.) Cross Site Request Forgery (CSRF). Available from: https://owasp.org/www-community/attacks/csrf [Accessed on 8/03/2022]

## Reply to a comment

> I started wondering how we can prevent MITM attacks as it seems that they are very challenging to spot once they are under way. It seems that one of the most effective protections against this kind of attack is using the latest TLS protocols when transferring data, rather than the outdated and vulnerable SSL 3.0 protocol which was deprecated in 2015.

It is easy to generate a pair of SSL/TLS keys, but it is impossible to derive one from the other in a short time. For this reason, it is safe to share one. Only the owner of the private key can decipher a message, and this makes the communication secure. This concept is the base of SSL/TLS certificates.

The weak point of the system is the authenticity of the certificate itself because an attacker could perform a man-in-the-middle and give his certificate to the victim. Certification Authorities (CA) solve the problem by signing the valid certificates. The browser issues warnings when it downloads a certificate without the signature of a trusted CA.

This, however, only moves the weak point to the authenticity of the CA. Browsers come with preinstalled CA certificates, but an attacker could always inject a malevolent CA into the browsers. Ironically, this is what often happens in enterprises. A company may create a custom CA and install it into all computers. That allows for internally signed certificates but also deep packet inspection. Employees may think that their HTTPS connections are private while browsing in the office, but in reality, a transparent proxy may perform a man-in-the-middle using the company's CA.
