# Events

## <a name= "onconnection">onConnection </a>

To receive various states during the connection from client to server.

### Type

**object**

### Properties

| Name | Type | Description |
|---|---|---|
| `state` | String | Different connection states below: <br> - **connecting**: Raised when connection starts before displaying connection dialog. <br> - **connected**: Raised when connection is complete and when server and client starts exchanging data. <br> - **sessionReady**: Raised when session is fully initialized, launched and ready for user interaction. |

### Example

```
//Sample event object generated for onConnection event.
{
	"id":"<session id>",
	"type" : "onConnection",
	"data":{
		"state" : "connecting" // Event is triggered 3 times with different states mentioned above.
	}
}
```

## <a name= "onconnectionclosed">onConnectionClosed</a>

Raised when the connection with the server is closed.

### Example
```
//Sample event object generated for onConnectionClosed event.
{
	"id":"<session id>",
	"type" : "onConnectionClosed",
}
```

## <a name ="onerror"> onError </a>

Raised on occurrence of any error in Citrix Workspace app for HTML5.

### Type

object

### Properties

| Name | Type | Description |
|---|---|---|
| `id` | String | String ID defined in <locale_file>.js. For example, en.js would be for English, ko.js for Korean etc., ID remains the same for all locales supported. |
| `message` |	 String |	Localized error message for the key. Customer can provide custom string in the language file to get meaningful error in the context of the deployment. |

### Example

```
//Sample event object generated for onError event.
{
	"id":"<session id>",
	"type" : "onError",
	"data":{
			"id":"<key_in_locale_file>"
			"message" : "<value_for_the_key_in_locale_file>"
		}
}	
```
						
## onToolbarBtnClick_btn_id

Raised when the custom toolbar button with id equal to btn_id is clicked.

### Example

```
//Sample event object generated for onConnectionClosed event.
{
	"id":"<session id>",
	"type" : "onToolbarBtnClick_btn_id",
	"data" : {
			"id" : <btn_id>
	}
}
```

## <a name= "onurlredirection">onURLRedirection</a> 

Raised when URL redirection is configured on server and when any URL is passed to the HTML5 engine to process. The message would contain the URL that is redirected to the client.

### Type

object

### Properties

| Name | Type | Description |
|---|---|---|
| `url` |	String | The value of the url would contain the URL that is redirected to the client. |

### Example

```
//Sample event object generated for onURLRedirection event.
{
	"id":"<session id>",
	"type" : "onURLRedirection",
	"data":{
		"url" : "<url_received_to_redirect>"
	}
}
```