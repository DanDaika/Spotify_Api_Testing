# Spotify_Api_Testing
Test Spotify API endpoints, using POSTMAN.

------------------------------

Current issues:
	- Environment variable naming (keys) needs to be standardized so that they will run accross all test suites
	- Test suits need to be modified on both contribuitor's end so that they will accept the standardized key names

------------------------------

SETUP FOR NEW TESTER
Steps on how to obtain the "client_id" and "secret_id" can be found here: https://developer.spotify.com/documentation/general/guides/app-settings/

Steps needed to generate the first access code can be found here:
	- https://developer.spotify.com/documentation/general/guides/app-settings/
	- I would recommend using the following callback uri: redirect_uri=https%3A%2F%2Fwww.getpostman.com%2Foauth2%2Fcallback
		- Add this to the whitelist as written in the above mentioned url.

Steps needed to generate the refresher token for a new user can be found here (2nd paragraph Have your application request refresh and access tokens; Spotify returns access and refresh tokens):
	- https://developer.spotify.com/documentation/general/guides/authorization-guide/
	
	