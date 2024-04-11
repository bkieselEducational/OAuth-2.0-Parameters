[<-- BACK](https://github.com/bkieselEducational/OAuth-2.0-from-Scratch)

# OAuth 2.0 Parameters

### access_type:

* `online` - It indicates that the application wants to access the user's data when they are present and interacting with the application. It may prompt the user to authenticate every time they use the application.

* `offline` - Setting this value to offline indicates that the application wants access to the user's data wether they are active in the app or not. This tells the API that we want to obtain a Refresh Token in addition to the Access Token.

> [!TIP]
> While the 'online' setting is considered 'default', most SDKs will actually set this value for you under the hood and they will likely set it to 'offline' so that you get a Refresh Token. If you have no use case for the Refresh Token, you may consider setting this explicitly yourself to 'online'.

### client_id:
- The id assigned to your application to access the OAuth API services.

### client_secret:
- The secret assigned to your application upon registration. It will be used at later stages of the OAuth flow to further validate your client.

### grant_type:

* `authorization_code` - For authorization code grants (Access Token).

* `client_credentials` - For client credentials grant.

* `password` - For the resource owner password crednetials grant.

* `refresh_token` - For refreshing an Access Token (using a Refresh Token)

### prompt:

* `consent` - This signals that the user authenticating to your app should be presented with the consent screen after successful login to verify the app in question.

* `login` - This indicates that the user will need to login with the provider of the OAuth API.

* `none` - Indicates that the vendor should not display authentication or consent pages. Use this only when you set id_token_hint and response_type=none.

> [!IMPORTANT]
> Note that the 3 values listed above are generic values that most OAuth APIs will recognize and honor, however each vendor may have it's own values that can be assigned here, for example the 'select_account' option offered by Google. Check the vendor's documentation if you are interested in more proprietary options!

### response_type:

* `code` - tells the auth endpoint that we want to obtain an authorization code that we can exchange for an access token.

* `id_token` - Here we are requesting an ID Token for an Implicit Grant Flow.

* `none` - The API will not return a code or an id token. This is use with id_token_hint only.

* `token` - This indicates that we want an access token for an Implicit Grant.
> [!IMPORTANT]
> This parameter can take multiple values, so the following are also legal settings: `code token id_token` `code token` `code id_token` `token id_token`

### scope:
> [!NOTE]
> Because the values for this parameter are very vendor specific, we will list the legal values for this parameter under the resources for that particular vendor.

# OAuth 2.0 Parameters for Security:
> [!NOTE]
> Generic Security

### nonce:
- A random string of any construction to be used as an additional layer of security when requesting an id_token from OpenID Connect. This will be returned in the claims of the JWT which is the id_token, so that you can further validate the integrity of the received data.

### state:
- A random alphanumeric string to use for CSRF protection as we initialize the flow using the Front-Channe (Browser URL Bar).

> [!IMPORTANT]
> PKCE Security

### code_verifier:
- A random string with a recommended variable length between 43-128 characters. 

### code_challenge:
- The base64URL encoded version of the SHA256 hashed code_verifier

### code_challenge_method:
* `plain` - This indicates a plain text encoding for the challenge. I'm not sure how I feel about that...

* `S256` - This indicates that the code_challenge was generated using the SHA256 hashing algorithm




