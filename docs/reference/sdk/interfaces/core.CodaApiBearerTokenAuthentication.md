---
nav: "CodaApiBearerTokenAuthentication"
note: "This file is autogenerated from TypeScript definitions. Make edits to the comments in the TypeScript file and then run `make docs` to regenerate this file."
search:
  boost: 0.1
---
# Interface: CodaApiBearerTokenAuthentication

[core](../modules/core.md).CodaApiBearerTokenAuthentication

Authenticate using a Coda REST API token, sent as an HTTP header.

This is identical to [HeaderBearerToken](../enums/core.AuthenticationType.md#headerbearertoken) except the user wil be presented
with a UI to generate an API token rather than needing to paste an arbitrary API
token into a text input.

This is primarily for use by Coda-authored packs, as it is only relevant for interacting with the
Coda REST API.

## Hierarchy

- [`BaseAuthentication`](core.BaseAuthentication.md)

  ↳ **`CodaApiBearerTokenAuthentication`**

## Properties

### deferConnectionSetup

• `Optional` **deferConnectionSetup**: `boolean`

If true, does not require a connection to be configured in
order to install the pack.

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

### networkDomain

• `Optional` **networkDomain**: `string` \| `string`[]

Which domain(s) should get auth credentials, when a pack is configured with multiple domains.
Packs configured with only one domain or with requiredsEndpointUrl set to true can omit this.

Using multiple authenticated network domains is uncommon and requires Coda approval.

#### Inherited from

[BaseAuthentication](core.BaseAuthentication.md).[networkDomain](core.BaseAuthentication.md#networkdomain)

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

### shouldAutoAuthSetup

• `Optional` **shouldAutoAuthSetup**: `boolean`

If true, automatically creates and configures an account with a Coda API token with
default settings when installing the pack: a scoped read-write token, added to the doc
as a shared account that allows actions.

___

### type

• **type**: [`CodaApiHeaderBearerToken`](../enums/core.AuthenticationType.md#codaapiheaderbearertoken)

Identifies this as CodaApiHeaderBearerToken authentication.
