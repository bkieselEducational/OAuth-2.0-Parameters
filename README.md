# OAuth-2.0-Parameters

### access_type:

* `online` - It indicates that the application wants to access the user's data when they are present and interacting with the application. It may prompt the user to authenticate every time they use the application.

* `offline` - Setting this value to offline indicates that the application wants access to the user's data wether they are active in the app or not. This tells the API that we want to obtain a Refresh Token in addition to the Access Token.

> [!TIP]
> While the online setting is considered 'default', most SDKs will actually set this value for you under the hood and they will likely set it to 'offline' so that you get a Refresh Token. If you have no use case for the Refresh Token, you may consider setting this explicitly yourself to 'online'.

### grant_type:

* `authorization_code` - For authorization code grants (Access Token).

* `client_credentials` - For client credentials grant.

* `password` - For the resource owner password crednetials grant.

* `refresh_token` - For refreshing an Access Token (using a Refresh Token)


### response_type:

* `code` - tells the auth endpoint that we want to obtain an authorization code that we can exchange for an access token.

* `id_token` - Here we are requesting an ID Token for an Implicit Grant Flow.

* `none` - The API will not return a code or an id token. This is use with id_token_hint only.

* `token` - This indicates that we want an access token for an Implicit Grant.
> [!IMPORTANT]
> This parameter can take multiple values, so the following are also legal settings: `code token id_token` `code token` `code id_token` `token id_token`

