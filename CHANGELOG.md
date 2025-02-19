# 5.1.0

-[#64](https://github.com/okta/okta-oidc-middleware/pull/64) Added type declarations

# 5.0.1

-[#60](https://github.com/okta/okta-oidc-middleware/pull/60) chore: dependency updates
-[#61](https://github.com/okta/okta-oidc-middleware/pull/60) chore: adds Node 18 support

# 5.0.0

### Breaking Changes

- [#]() Requires Node >= 12.19.0. Update production dependencies:
  - `openid-client@5.1.9` (was 3.12.2)

# 4.6

-[#53](https://github.com/okta/okta-oidc-middleware/pull/53) Fix: prevents open redirects

# 4.5.1

### Bug Fixes

- [#43](https://github.com/okta/okta-oidc-middleware/pull/43) fix: correctly preprends `appBaseUrl` to redirect url when `appBaseUrl` contains a base path

# 4.5.0

### Features

- [#40](https://github.com/okta/okta-oidc-middleware/pull/40) Allows passing `loginHint` to `ensureAuthenticated`

### Bug Fixes

- [#42](https://github.com/okta/okta-oidc-middleware/pull/42) Fixes `appBaseUrl` option not prepending to login redirect url

# 4.4.0

### Bug Fixes

- [#34](https://github.com/okta/okta-oidc-middleware/pull/34) Fixes Org AS login issue
- [#3](https://github.com/okta/okta-oidc-middleware/pull/3) Call `res.redirect()` after custom `routes.loginCallback.handler`
- [#37](https://github.com/okta/okta-oidc-middleware/pull/37) fix: `.logout` no longer throws error without valid credentials

# 4.3.0

### Other

- Release after migrating from monorepo
- 
# 4.2.0

### Bug Fixes

- [#1020](https://github.com/okta/okta-oidc-js/pull/1020) Fixes issue with UUID returning null

# 4.1.0

### Features

- [#989](https://github.com/okta/okta-oidc-js/pull/989) adds callback to allow custom error handling
  
# 4.0.3

### Bug Fixes

- [#962](https://github.com/okta/okta-oidc-js/pull/962)
  - fixes options.timeout for requests to /token
  
# 4.0.2

### Bug Fixes

- [#949](https://github.com/okta/okta-oidc-js/pull/949) 
  - oidcUtil: support for passport strategy callback without userinfo

# 4.0.1

### Bug Fixes

- [#731](https://github.com/okta/okta-oidc-js/pull/731) 
  - Fix redirect issue after login 
  - Remove dependency `connect-ensure-login`

# 4.0.0

### Breaking Changes

- [#661](https://github.com/okta/okta-oidc-js/pull/661) Requires Node >= 10.13.0. Add support for Node 12. Update production dependencies:
  - `openid-client@3.12.2` (was 2.5.0)
  - `passport@0.4.1` (was 0.3.2)
  - `@okta/configuration-validation@0.4.1` (was 0.2.0)

# 3.0.0

### Breaking Changes 

See "Updating" in the README for migration steps

- Logout callback route has been removed (`/logout/callback`). Local session is now cleared before redirect to Okta and the default logout redirect Uri is the app base URL. [#644](https://github.com/okta/okta-oidc-js/pull/644)

# 2.1.0

### Features

- Support for Org Authorization Servers. [#590](https://github.com/okta/okta-oidc-js/pull/590) - See [composing your base url](https://developer.okta.com/docs/reference/api/oidc/#composing-your-base-url) for more information on Authorization Servers.

### Bug Fixes
- Errors during logout would cause the user to receive an empty page and remain logged in. [#585](https://github.com/okta/okta-oidc-js/pull/585) - 

  Due to this bug, errors during logout were being incorrectly suppressed and would not have been seen by the server process. Instead, the user would see a blank page. With this fix, the user will be logged out correctly, but the error event will also now be emitted to the server process.

  Your server code should be prepared to either log or ignore this error.

# 2.0.0

### Features

- [`a4b54f7`](https://github.com/okta/okta-oidc-js/commit/a4b54f771e19f2eeece46a39ded135550061f2a1) - adds Okta logout capability

- [`a999b95`](https://github.com/okta/okta-oidc-js/commit/a999b959c98bfea2f138281b2f93efb2d2d5fac7) - adds appBaseUrl, removes redirect_uri

- Adds Okta logout capability (informing Okta that the session is ended rather than just locally forgetting the current session) ([#162](https://github.com/okta/okta-oidc-js/issues/162))

### Breaking Changes 

See "Updating" in the README for migration steps

- `redirect_uri` config option is dropped.  The value is either automatically derived from the `appBaseUrl` and the appropriate `routes` option, or explicitly set as `loginRedirectUri`
- Two new routes are automatically generated and will override manually created routes of the same path.  Unless `routes` is customized, they are `/logout` (POST only) and `/logout/callback`
- `routes.callback` is renamed to `routes.loginCallback`
- `routes.callback.defaultRedirect` is renamed to `routes.loginCallback.afterCallback`

# 1.0.2

### Other

- [`2945461`](https://github.com/okta/okta-oidc-js/pull/338/commits/294546166a41173b699579d7d647ba7d5cab0764) - Updates `@okta/configuration-validation` version.

# 1.0.1

### Features

- [`ed29bf5`](https://github.com/okta/okta-oidc-js/pull/320/commits/ed29bf5f1618a7b6941b8a4d47160fac7fb3f749) - Adds configuration validation for `issuer`, `client_id`, `client_secret`, and `redirect_uri` when passed into the middleware.

### Other

- [`c37b9cf`](https://github.com/okta/okta-oidc-js/pull/326/commits/c37b9cf483e17720b233800b8b5609c3383b8167) - Updates the TCK version to support new integration tests.
- [`3582f25`](https://github.com/okta/okta-oidc-js/pull/318/commits/3582f259cf74dbb45b6eed673065c2d3c03e9db3) - Rely on shared environment configuration from project root.
- [`c8b7ab5a`](https://github.com/okta/okta-oidc-js/commit/c8b7ab5aacecf5793efb6a626c0a24a78147ded9#diff-b8cfe5f7aa410fb30a335b09346dc4d2) - Migrate dependencies to project root utilizing [yarn workspaces](https://yarnpkg.com/lang/en/docs/workspaces/).
- [`8494be0`](https://github.com/okta/okta-oidc-js/pull/292/commits/8494be0ec98887d19870941d2a0ddbf653dbbb6c) - Migrate mocha tests to jest.

# 1.0.0

### Features

- Attach the requested tokens to the user context object ([#226](https://github.com/okta/okta-oidc-js/issues/226))

  ```javascript
  app.get('/', (req, res) => {
    if (req.userContext) {
      const tokenSet = req.userContext.tokens;
      const userinfo = req.userContext.userinfo;

      console.log(`Access Token: ${tokenSet.access_token}`);
      console.log(`Id Token: ${tokenSet.id_token}`);
      console.log(`Claims: ${tokenSet.claims}`);
      console.log(`Userinfo Response: ${userinfo}`);

      res.send(`Hi ${userinfo.sub}!`);
    } else {
      res.send('Hi!');
    }
  });
  ```

- Basic configuration validation for catching common input mistakes.

### Breaking Changes

- `req.userinfo` is now nested within `req.userContext` ([#226](https://github.com/okta/okta-oidc-js/issues/226)). Please update any use of `req.userinfo` to `req.userContext.userinfo`.

# 0.1.3

### Bug Fixes

- Removed next() in ensureAuthenticated ([#224](https://github.com/okta/okta-oidc-js/issues/224)) ([592ec42](https://github.com/okta/okta-oidc-js/commit/592ec420a4afcf12cbae5d04774502820e326b98))

### Other

- Updating openid-client dependency ([#222](https://github.com/okta/okta-oidc-js/issues/222)) ([8047386](https://github.com/okta/okta-oidc-js/commit/8047386519ca34ac4b6674d7e6a9b0e60a95de06/))
