---
nav: "OAuth2Authentication"
note: "This file is autogenerated from TypeScript definitions. Make edits to the comments in the TypeScript file and then run `make docs` to regenerate this file."
search:
  boost: 0.1
---
# Interface: OAuth2Authentication

[core](../modules/core.md).OAuth2Authentication

Authenticate using OAuth2. You must specify the authorization URL, token exchange URL, and
scopes here as part of the pack definition. You'll provide the application's client ID and
client secret in the pack management UI, so that these can be stored securely.

The API must use a (largely) standards-compliant implementation of OAuth2.

## Hierarchy

- [`BaseAuthentication`](core.BaseAuthentication.md)

  ↳ **`OAuth2Authentication`**

## Properties

### additionalParams

• `Optional` **additionalParams**: `Object`

Option custom URL parameters and values that should be included when redirecting the
user to the [authorizationUrl](core.OAuth2Authentication.md#authorizationurl).

#### Index signature

▪ [key: `string`]: `any`

___

### authorizationUrl

• **authorizationUrl**: `string`

The URL to which the user will be redirected in order to authorize this pack.
This is typically just a base url with no parameters. Coda will append the `scope`
parameter automatically. If the authorization flow requires additional parameters,
they may be specified using [additionalParams](core.OAuth2Authentication.md#additionalparams).

___

### endpointDomain

• `Optional` **endpointDomain**: `string`

When requiresEndpointUrl is set to true this should be the root domain that all endpoints share.
For example, this value would be "example.com" if specific endpoints looked like {custom-subdomain}.example.com.

For packs that make requests to multiple domains (uncommon), this should be the domain within
[networkDomains](core.PackVersionDefinition.md#networkdomains) that this configuration applies to.

#### Inherited from

[BaseAuthentication](core.BaseAuthentication.md).[endpointDomain](core.BaseAuthentication.md#endpointdomain)

___

### endpointKey

• `Optional` **endpointKey**: `string`

In rare cases, OAuth providers will return the specific API endpoint domain for the user as
part of the OAuth token exchange response. If so, this is the property in the OAuth
token exchange response JSON body that points to the endpoint.

The endpoint will be saved along with the account and will be available during execution
as [endpoint](core.ExecutionContext.md#endpoint).

___

### getConnectionName

• `Optional` **getConnectionName**: [`MetadataFormula`](../types/core.MetadataFormula.md)

A function that is called when a user sets up a new account, that returns a name for
the account to label that account in the UI. The users credentials are applied to any
fetcher requests that this function makes. Typically, this function makes an API call
to an API's "who am I" endpoint and returns a username.

If omitted, or if the function returns an empty value, the account will be labeled
with the creating user's Coda username.

#### Inherited from

[BaseAuthentication](core.BaseAuthentication.md).[getConnectionName](core.BaseAuthentication.md#getconnectionname)

___

### instructionsUrl

• `Optional` **instructionsUrl**: `string`

A link to a help article or other page with more instructions about how to set up an account for this pack.

#### Inherited from

[BaseAuthentication](core.BaseAuthentication.md).[instructionsUrl](core.BaseAuthentication.md#instructionsurl)

___

### nestedResponseKey

• `Optional` **nestedResponseKey**: `string`

In rare cases, OAuth providers send back access tokens nested inside another object in
their authentication response.

___

### networkDomain

• `Optional` **networkDomain**: `string` \| `string`[]

Which domain(s) should get auth credentials, when a pack is configured with multiple domains.
Packs configured with only one domain or with requiredsEndpointUrl set to true can omit this.

Using multiple authenticated network domains is uncommon and requires Coda approval.

#### Inherited from

[BaseAuthentication](core.BaseAuthentication.md).[networkDomain](core.BaseAuthentication.md#networkdomain)

___

### pkceChallengeMethod

• `Optional` **pkceChallengeMethod**: ``"plain"`` \| ``"S256"``

See [useProofKeyForCodeExchange](core.OAuth2Authentication.md#useproofkeyforcodeexchange)

___

### postSetup

• `Optional` **postSetup**: [`SetEndpoint`](core.SetEndpoint.md)[]

One or more setup steps to run after the user has set up the account, before completing installation of the pack.
This is not common.

#### Inherited from

[BaseAuthentication](core.BaseAuthentication.md).[postSetup](core.BaseAuthentication.md#postsetup)

___

### requiresEndpointUrl

• `Optional` **requiresEndpointUrl**: `boolean`

If true, indicates this has pack has a specific endpoint domain for each account, that is used
as the basis of HTTP requests. For example, API requests are made to <custom-subdomain>.example.com
rather than example.com. If true, the user will be prompted to provide their specific endpoint domain
when creating a new account.

#### Inherited from

[BaseAuthentication](core.BaseAuthentication.md).[requiresEndpointUrl](core.BaseAuthentication.md#requiresendpointurl)

___

### scopeDelimiter

• `Optional` **scopeDelimiter**: ``" "`` \| ``","`` \| ``";"``

The delimiter to use when joining [scopes](core.OAuth2Authentication.md#scopes) when generating authorization URLs.

The OAuth2 standard is to use spaces to delimit scopes, and Coda will do that by default.
If the API you are using requires a different delimiter, say a comma, specify it here.

___

### scopeParamName

• `Optional` **scopeParamName**: `string`

In rare cases, OAuth providers may want the permission scopes in a different query parameter
than `scope`.

___

### scopes

• `Optional` **scopes**: `string`[]

Scopes that are required to use this pack.

Each API defines its own list of scopes, or none at all. You should consult
the documentation for the API you are connecting to.

___

### tokenPrefix

• `Optional` **tokenPrefix**: `string`

A custom prefix to be used when passing the access token in the HTTP Authorization
header when making requests. Typically this prefix is `Bearer` which is what will be
used if this value is omitted. However, some services require a different prefix.
When sending authenticated requests, a HTTP header of the form
`Authorization: <tokenPrefix> <token>` will be used.

___

### tokenQueryParam

• `Optional` **tokenQueryParam**: `string`

In rare cases, OAuth providers ask that a token is passed as a URL parameter
rather than an HTTP header. If so, this is the name of the URL query parameter
that should contain the token.

___

### tokenUrl

• **tokenUrl**: `string`

The URL that Coda will hit in order to exchange the temporary code for an access token
at the end of the OAuth handshake flow.

___

### type

• **type**: [`OAuth2`](../enums/core.AuthenticationType.md#oauth2)

Identifies this as OAuth2 authentication.

___

### useProofKeyForCodeExchange

• `Optional` **useProofKeyForCodeExchange**: `boolean`

Option to apply PKCE (Proof Key for Code Exchange) OAuth2 extension. With PKCE extension,
a `code_challenge` parameter and a `code_challenge_method` parameter will be sent to the
authorization page. A `code_verifier` parameter will be sent to the token exchange API as
well.

`code_challenge_method` defaults to SHA256 and can be configured with [pkceChallengeMethod](core.OAuth2Authentication.md#pkcechallengemethod).

See https://datatracker.ietf.org/doc/html/rfc7636 for more details.
