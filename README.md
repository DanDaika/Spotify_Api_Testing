Spotify_Api_Testing
===================
 - Test Spotify API endpoints, using POSTMAN
 - POSTMAN for WINDOWS v7.9.0

Version 1.0
-----------
	- New environment variables template has been created
	- All tests suites run with the standardized environment variables
	- Version added for the current document

SETUP FOR NEW TESTER
--------------------
 + Steps on how to obtain the "client_id" and "secret_id" can be found here: https://developer.spotify.com/documentation/general/guides/app-settings/
 + A new non-commercial application needs to be created within your spotify account for you to recieve both client_id and your client_secret. Both of these will be important later on for you to obtain your authentification
and refresher token
1. Create a new Spotify User account at the following link: https://www.spotify.com
2. Using the created account login on the Dashboard : https://developer.spotify.com/dashboard
3. Create a client ID in order to get your Client ID and Client Secret
4. Select the new created application and go to 'EDIT SETTINGS'. Here complete the 'Redirect URIs' with: https://www.getpostman.com/oauth2/callback

SETUP TO OBTAIN THE CODE
------------------------
***Without POSTMAN***

 + Steps needed to generate the first access "code" can be found here: https://developer.spotify.com/documentation/general/guides/app-settings/
 + Before you can get the CODE you need to manually grant access to your account. You do that by using the following link: 
	https://accounts.spotify.com/authorize?client_id={{client_id}}&response_type=code&redirect_uri={{redirect_uri}}&state={{state}}&scope={{scopes}}&show_dialog=false
 + Here you replace the following:
	 - {{client_id}} 		**with** 	 the one obtained when seting up a new tester
	 - {{redirect_uri}} 		**with**	 https://www.getpostman.com/oauth2/callback
	 - {{state}} 			**with**	 the country
	 - {{scope}} 			**with**	 the scopes for which you need access
 + NOTE: With the help of this callback URI, you'll be able to retrieve you're authorization code and refresher token. Of course you can use other URIs as well. Just make sure you update the settings for the API you created earlier and the environment variable
 + NOTE: At this point, no UI test automation is in place, so you'll have to manually accept the authorization request
 + NOTE: Scopes are very important when retreiving your authorization code. Scopes will define what you can and what you cannot do later on and will affect the running of test suites
 + To be able to run all the created test cases please provide all the scopes available: 
		*playlist-read-collaborative playlist-modify-private playlist-modify-public 
		playlist-read-private user-modify-playback-state user-read-currently-playing 
		user-read-playback-state user-read-private user-read-email user-library-modify 
		user-library-read user-follow-modify user-follow-read user-read-recently-played 
		user-top-read streaming app-remote-control*
 + You can find a list of scopes in this link: https://developer.spotify.com/documentation/general/guides/scopes
 + After granting access to your account you will get the CODE in the returned URL. Further on you can exchange this CODE for the TOKEN and REFRESH_TOKEN
 
***With POSTMAN***

1. From Base Tests folder get the following POSTMAN collection: Get the CODE, the TOKEN and the REFRESH TOKEN
2. From Environment Variables folder get the following POSTMAN environment: Spotify_API_Template
3. Start POSTMAN and import the collection and the environment
4. Open the Spotify_API_Template in order to fill in the user specific variables. This are as follows:
				- user_id 					the Spotify User created when setting up the new tester
				- other_user_id				any other valid Spotify User
				- client_id					the Client ID obtained after creating the client ID(may sound redundant, but this are the names)
				- client_secret				the Client Secret obtained after creating the client ID
				- state						country
5. Open the POSTMAN console
6. From the POSTMAN application send the 'Get Code' request, while Spotify_API_Template environment is selected
7. From the POSTMAN console copy the generated URL and paste it in a browser
8. A web page with a request to allow access to your account should be available. For the tests to run you should grant access
9. After granting access, a new URL is generated which contains the requested CODE. Save this CODE in POSTMAN Spotify_API_Template environment, under the code alias
 + NOTE: This manual granting needs to be performed once for any scope. You can grant access for more scopes at once
 + NOTE: Once you manually granted access to a scope/scopes you can use POSTMAN script to generate a new CODE for the same scope/scopes. The code variable from the Spotify_API_Template environment will be updated
 + NOTE: You can use the CODE only once, to exchange it for the TOKEN and REFRESH_TOKEN
	
SETUP TO OBTAIN TOKEN AND REFRESH_TOKEN
---------------------------------------
 + Steps needed to generate the refresher token for a new user can be found here (2nd paragraph Have your application request refresh and access tokens; Spotify returns access and refresh tokens):
	- https://developer.spotify.com/documentation/general/guides/authorization-guide/
 + Once you obtained the CODE, use it to send a POST request in POSTMAN. This way you will exchange it for a TOKEN and a REFRESH_TOKEN.
1. From Base Tests folder get the following POSTMAN collection: Get the CODE, the TOKEN and the REFRESH TOKEN
2. From Environment Variables folder get the following POSTMAN environment: Spotify_API_Template
3. Start POSTMAN and import the collection and the environment
4. Make sure the code environment variable is filled in, in the Spotify_API_Template environment
5. From the POSTMAN application send the 'Get Token and Refresh_token' request, while Spotify_API_Template environment is selected
6. The token and refresh_token variables from the Spotify_API_Template environment should be updated with the new values
 + NOTE: The TOKEN is valid for only one hour. After one hour a new TOKEN needs to be generated with the help of the REFRESH_TOKEN
 + NOTE: The REFRESH_TOKEN shouldn't expire. But if by any chance it doesn't work any more, just get a new CODE and generate yourself a new TOKEN and REFRESH_TOKEN

Explanation of environment variables
------------------------------------
	+ "user_id" 						- a valid Spotify user ID. Initially it would be recomended that you give your own user ID
	+ "other_user_id" 					- any other valid Spotify user ID
	+ "client_id"  						- the Client ID obtained when creating a new Client ID
	+ "client_secret"					- the Client Secret obtained when creating a new Client ID
	+ "state" 						- country
	+ "accounts_domain"					- Spotify accounts endpoint domain (https://accounts.spotify.com)
	+ "api_domain" 						- Spotify API endpoint domain (https://api.spotify.com)
	+ "redirect_uri"					- a redirect uri to be able to get the CODE
	+ "scopes"						- areas where the user grants access
	+ "code"						- the CODE needed to get the TOKEN and REFRESH_TOKEN
	+ "token"						- the TOKEN needed to interact with the Spotify API endpoint
	+ "refresh_token"					- the REFRESH_TOKEN needed to refresh the TOKEN every hour, when it expires
	+ "artist_id_1"						- Spotify artist id, can be any valid artist id
	+ "artist_id_2"						- Spotify artist id, can be any valid artist id
	+ "album_id_1"						- Spotify album id, can be any valid album id
	+ "album_id_2"						- Spotify album id, can be any valid album id
	+ "track_id_1"						- Spotify track id, can be any valid track id
	+ "track_id_2"						- Spotify track id, can be any valid track id
	+ "playlist_id"						- Spotify playlist id, can be any valid playlist id 
	+ "contained_album"					- Spotify album id, can be any valid album id
	+ "album_not_contained"					- can be any invalid album id
	+ "incorrect_album_uris"				- wrong uris for an album id
	+ "existing_album_id"					- Spotify album id, can be any valid album id
	+ "incorrect_artist_id"					- wrong artist id
	+ "search_item"						- the searched item
	+ "search_type"						- the type of the searched item
	+ "albumsGetAlbumSchema"				- JSON schema
	+ "falseSchema"						- JSON schema
	+ "albumsGetAnAlbumsTracks" 				- JSON schema
	+ "json_schema_for_new_release" 			- JSON schema
	+ "category_id_1"					- the category in Spotify

SETUP TO RUN TESTS
------------------
1. From Tests folder get the desired POSTMAN collection
2. Start POSTMAN and run once the following collection 'Get the CODE, the TOKEN and the REFRESH TOKEN'.Make sure you have the 'Spotify_API_Template' environment and that you have all the variables from the environment filled in
If you have missing variables please read the SETUP steps above
3. Import the collection you want to test
4. Run the collection you want to test
5. When using the POSTMAN Runner make sure you have the following settings in it:
	- Select the correct environment
	- 'Keep variables values' checked
	- 'Save cookies after collection run' checked 