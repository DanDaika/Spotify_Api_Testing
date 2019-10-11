# Spotify_Api_Testing
Test Spotify API endpoints, using POSTMAN.

------------------------------

Current version
	- New environment variables template has been created
	- All tests suites run with the standardized environment variables
	

------------------------------

Steps needed to generate the refresher token for a new user can be found here (2nd paragraph Have your application request refresh and access tokens; Spotify returns access and refresh tokens):
	- https://developer.spotify.com/documentation/general/guides/authorization-guide/
	
------------------------------

SETUP FOR NEW TESTER

Steps on how to obtain the "client_id" and "secret_id" can be found here: https://developer.spotify.com/documentation/general/guides/app-settings/
	- Note: A new non-commercial application needs to be created within your spotify account for you to recieve both client_id and your secret_id. Both of these will be important later on for you to obtain your authentification
	and refresher token.

Steps needed to generate the first access code can be found here:
	- https://developer.spotify.com/documentation/general/guides/app-settings/
	- I would recommend using the following callback uri: redirect_uri=https%3A%2F%2Fwww.getpostman.com%2Foauth2%2Fcallback
		- Add this to the whitelist as written in the above mentioned url.
		- Note: with the help of this callback URI, you'll be able to retrieve you're authorization code and refresher token.
		- Note: at this point, no UI test automation is in place, so you'll have to manually accept the authorization request.
		- Note: Scopes are very important when retreiving your authorization code. Scopes will define what you can and what you cannot do later on and will affect the running of test suites.
		- Note: you can find a <a href="https://developer.spotify.com/documentation/general/guides/scopes/" =>list of scopes in this link here </a>.
	
Steps needed to generate the refresher token for a new user can be found here (2nd paragraph Have your application request refresh and access tokens; Spotify returns access and refresh tokens):
	- https://developer.spotify.com/documentation/general/guides/authorization-guide/
	

------------------------------

Explenation of environment variables
	An explenation of all the environment variables will be available below:
	+ "user_id" - the user ID you're looking for. Initially it would be recomended that you give your own user id
	+ "api_domain" - the API endpoint domain. By default it should be: "https://api.spotify.com"
	To be continued.
	
	