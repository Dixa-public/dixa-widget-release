# Dixa widget releases

This is the repo for hosting the releases for self-hosting Dixa widget. Each release will be added to the [release section in this repo](https://github.com/Dixa-public/dixa-widget-release/releases). 
These release packages are recommended for customers who need to host and control the version of the widget themself. If you don't need that control please use the default setup found in [Dixa settings](https://support.dixa.help/en/articles/64-install-the-chat-widget-script-on-your-website).

Breaking changes will be announced on this page a month before the changes will be introduced.

* The release uses semver https://semver.org
* The changelog can be found in the [release section](https://github.com/Dixa-public/dixa-widget-release/releases)

### Sign-in user with a token
It's possible to sign-in a user token on a JWT token. This a safe way to validate the user. A secret is shared between Dixa and the customer organization. Only the token is stored in the widget state.

```javascript 
window._dixa("api.setUserToken", JWT_TOKEN);
```

The widget keeps the token in its state until the user is signed out. If an conversation is active in the widget the `window._dixa("api.setUserToken", JWT_TOKEN);` request is ignored.

### Dynamic imports path at runtime
`dixaPublicPath` is the globally defined variable that will be evaluated at runtime. `window.dixaPublicPath` is the name of a variable with a string value that represents a path / URL that will be used for dynamically importing of chunks.

For example, if default URL is `https://widget.dixa.io/assets/scripts/javascript/`, one of the chunk name is eg. `main.[hash].js`. Changing the ` window.dixaPublicPath` variable value: to eg. `https://mydomain.com/folder/` result in the chunk file would fetched from `https://mydomain.com/folder/main.[hash].js`.

```javascript
// The chunk will be fetched from https://mydomain.com/folder/main.[hash].js
window.dixaPublicPath = "https://mydomain.com/folder/";
```
