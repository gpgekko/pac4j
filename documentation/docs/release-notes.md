---
layout: doc
title: Release notes&#58;
---

**v1.9.4**:

- Critical security issue since the version 1.9.2 on the `NopPasswordEncoder` regarding the `MongoAuthenticator` and the `DbAuthenticator`: upgrading is mandatory

**v1.9.3**:

- Bug fixes (`Authenticator` initialization, `resource:` / `classpath:` prefixes in the SAML support...)
- New `HeaderMatcher` and `HttpMethodMatcher`
- The `Config` holds a `SecurityLogic`
- The OpenID Connect configuration can be done without a discovery URL
- The Dropbox support uses the OAuth protocol v2.0
- The expiration time is checked on JWT, as well as the existence of the subject
- The `IpExtractor` can work on an alternative header name
- A specific profile can be built by the `AuthenticatorProfileCreator`

**v1.9.2**:

- the CAS support has been upgraded: the CAS configuration is defined via the `CasConfiguration`, the new `DirectCasProxyClient` must be used to validate proxy tickets, the front channel logout is supported by the `CasSingleSignOutHandler`, the OAuth support is compatible with CAS v5
- the JWT support has been upgraded: `SignatureConfiguration` classes allow to define HMac, RSA or Elliptic Curve signatures
- the OpenID Connect support has been upgraded: the OIDC configuration is defined via the `OidcConfiguration`, all standard claims are supported in the `OidcProfile`, most flows are supported
- CORS (AJAX) requests can be controlled via the `CorsAuthorizer` and its default pre-defined `allowAjaxRequests` name
- Profile attribute can be checked via the `RequireAnyAttributeAuthorizer`
- the `AjaxRequestResolver`,  `CallbackUrlResolver` and `AuthorizationGenerator` can be defined at the `Clients` level for all defined clients
- new implementations for the `PasswordEncoder` are available for Spring Security, Shiro or JBCrypt.

**v1.9.1**:

- the `Authenticator` and `ProfileCreator` have access to the web context
- the signature of the SAML authentication requests can be disabled

**v1.9.0**:

- Upgraded to Java 8 as well as all most dependency versions
- Removed useless concepts: client type, client cloning capabilities, raw data, direct/indirect redirection, proxy configuration for OAuth clients (to be set at the JVM level or by overriding the `OAuthRequest` class)
- All security logics are now available in the core via the `SecurityLogic`, `CallbackLogic` and `ApplicationLogoutLogic` components
- Any client can be built using the `RedirectActionBuilder`, `CredentialsExtractor`, `Authenticator` and `ProfileCreator` concepts (`DirectClientV2` and `IndirectClientV2`): to be re-used to build asynchronous clients
- `CredentialsExtractor`, `Authenticator`, `ProfileCreator` and `Authorizer` can throw `HttpAction` (previously named `RequiresHttpAction`) to break the flow and handle custom use cases
- Typed id are now defined using the full class name (with package): "org.pac4j.oauth.profile.facebook.FacebookProfile#id" instead of "FacebookProfile#id" (use the `getOldTypedId()` method to get the old value)
- Comparisons for clients / authorizers names are case insensitive and trimmed
- Most integration tests have been replaced by manual tests (RunXXX classes)
- Updated OpenID Connect support (`GoogleOidClient` and `AzureAdClient`)

[&#9656; Older versions...](release-notes-older.html)
