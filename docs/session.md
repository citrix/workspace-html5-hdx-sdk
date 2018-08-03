# Session

**new Session()**

## Members

### container

Contains the type and value of the container where the session is launched.

#### Properties

<table class="props">
    <thead>
    <tr>

        <th>Name</th>


        <th>Type</th>





        <th class="last">Description</th>
    </tr>
    </thead>

    <tbody>


        <tr>

                <td class="name"><code>container</code></td>


            <td class="type">


<span class="param-type">Object</span>



            </td>





            <td class="description last">
                <h6>Properties</h6>

<table class="props">
    <thead>
    <tr>

        <th>Name</th>


        <th>Type</th>





        <th class="last">Description</th>
    </tr>
    </thead>

    <tbody>


        <tr>

                <td class="name"><code>type</code></td>


            <td class="type">


<span class="param-type">String</span>



            </td>





            <td class="description last">Type of the container. Will be set to "iframe" or "window" when launchType is set to "embed" or "newtab" respectively.</td>
        </tr>



        <tr>

                <td class="name"><code>value</code></td>


            <td class="type">


<span class="param-type">Object</span>



            </td>





            <td class="description last">Contains the iframe DOM object or reference to the window where the session is launched based on the launchType.</td>
        </tr>


    </tbody>
</table>
</table>

### (readonly) id

#### Properties

| Name | Type | Description |
|---|---|---|
| `id` | String | ID of the object |

## Methods

### (inner) addListener(eventType, eventListener)

Registers the eventListener on the eventType.

#### Parameters

| Name | Type | Description |
|---|---|---|
| `eventType` | String | Type of the event for which the listener needs to be attached. Supported event types: <br> - [onConnection](./events#onconnection) <br> - [onConnectionClosed](./events#onconnectionclosed) <br> - [onURLRedirection](./events#onurlredirection) <br> - [onError](./events#onerror) |
| `eventListener` | [eventListener](./global#eventlistener) | Listener to handle the event |

#### Example 

```
// Adding onConnection event handler
function connectionHandler(event){
	console.log("Event Received : " + event.type);
	console.log(event.data);
}
sessionObject.addListener("onConnection",connectionHandler);

// Adding onConnectionClosed event handler
function connectionClosedHandler(event){
	console.log("Event Received : " + event.type);
	console.log(event.data);
}
sessionObject.addListener("onConnectionClosed",connectionClosedHandler);

// Adding onError event handler
function onErrorHandler(event){
	console.log("Event Received : " + event.type);
	console.log(event.data);
}
sessionObject.addListener("onError",onErrorHandler);

//Adding onURLRedirection event handler
function onURLRedirectionHandler(event){
	console.log("Event Received : " + event.type);
	console.log(event.data);
}
sessionObject.addListener("onURLRedirection",onURLRedirectionHandler);
```
### (inner) addToolbarBtns(customToolbarData)

Adds the custom buttons to the in-session toolbar.

#### Parameters

<table class="params">
    <thead>
    <tr>

        <th>Name</th>


        <th>Type</th>





        <th class="last">Description</th>
    </tr>
    </thead>

    <tbody>


        <tr>

                <td class="name"><code>customToolbarData</code></td>


            <td class="type">


<span class="param-type">Array.&lt;Object&gt;</span>



            </td>





            <td class="description last">Array of objects containing the custom toolbar buttons to be added where each object contains more details of the button to be added.<br><br><b> Note: Toolbar should be enabled to use this method.</b><br><br>
                <h6>Properties</h6>


<table class="params">
    <thead>
    <tr>

        <th>Name</th>


        <th>Type</th>





        <th class="last">Description</th>
    </tr>
    </thead>

    <tbody>


        <tr>

                <td class="name"><code>id</code></td>


            <td class="type">


<span class="param-type">String</span>



            </td>





            <td class="description last">id of the button</td>
        </tr>



        <tr>

                <td class="name"><code>config.isPrimary</code></td>


            <td class="type">


<span class="param-type">boolean</span>



            </td>





            <td class="description last">Value set to true specifies that the button to be added to primary toolbar buttons.<br> Setting to false would add to secondary menu (present under more button). <br><br>Defaults to true.</td>
        </tr>



        <tr>

                <td class="name"><code>config.imageUrl</code></td>


            <td class="type">


<span class="param-type">String</span>



            </td>





            <td class="description last">Image url of the button. Mandatory when the button is added to primary toolbar button.<br><br>Note:<br> Recommendation is to host the images where SDK files are hosted and give full path of the image. <br>Other option is to use the data URL of the image.<br><br>If the images are hosted in origin other than that of SDK then Content security policy in HDXEngine.html has to be edited to allow the images to be fetched.</td>
        </tr>



        <tr>

                <td class="name"><code>config.position</code></td>


            <td class="type">


<span class="param-type">String</span>



            </td>





            <td class="description last">Specifies the position of the custom button when added as primary toolbar button.For secondary custom buttons it would be appended to the menu shown on clicking more button.<br> <br>1) Setting to 'front' would add the button to the front of the toolbar (immediately after receiver button).<br>2) Setting to 'rear' would add the button before more button.<br><br> Note : For secondary custom buttons it would be appended to the menu shown on clicking more button.<br><br> Defaults to 'front' when unspecified.</td>
        </tr>



        <tr>

                <td class="name"><code>config.toolTip</code></td>


            <td class="type">


<span class="param-type">String</span>



            </td>





            <td class="description last">Value is set as tooltip if the custom button is primary. <br>For secondary the value is shown as the menu item.</td>
        </tr>



        <tr>

                <td class="name"><code>handler</code></td>


            <td class="type">


<span class="param-type"><a href="https://developer-docs.citrix.com/projects/receiver-html5-sdk/en/latest/global/#eventlistener">eventListener</a></span>



            </td>





            <td class="description last">Event listener that listens for the click of the custom toolbar button.</td>
        </tr>


    </tbody>
</table>

</table>

#### Examples

**Example 1:**  Adding help custom button to primary toolbar and position is set to rear(added before more button)

```
function helpButtonHandler(eventObj){
	console.log("Event Received : " + event.type);
	console.log(event.data);
}

var customToolbarData = [{"id" :"help","config":{"position":"rear","imageUrl":"http://<path_of_the_image>/help.png","toolTip":"Help"},"handler":helpButtonHandler}];
sessionObject.addToolbarBtns(customToolbarData);
```

**Example 2:** Adding back and forward buttons that allows navigation of the webpage in browser and position is set to front (added after Workspace app button).

```
function backButtonHandler(eventObj){
	console.log("Event Received : " + event.type);
	console.log(event.data);
	sessionObject.sendSpecialKeys(["ALT_KEY","LEFT_ARROW"]);
}
function forwardButtonHandler(eventObj){
	console.log("Event Received : " + event.type);
	console.log(event.data);
	sessionObject.sendSpecialKeys(["ALT_KEY","RIGHT_ARROW"]);
}

var customToolbarData = [];
customToolbarData.push({"id" :"back","config":{"position":"front","imageUrl":"http://<path_of_the_image>/back.png","toolTip":"Back"},"handler":backButtonHandler});
customToolbarData.push({"id" :"forward","config":{"position":"front","imageUrl":"http://<path_of_the_image>/fwd.png","toolTip": "Forward"},"handler":forwardButtonHandler});

sessionObject.addToolbarBtns(customToolbarData);<br/><br/><br/>
```

**Example 3:**  Adding help custom button as primary toolbar with position set to rear and contact us button as secondary button.

```
function helpButtonHandler(eventObj){
	console.log("Event Received : " + event.type);
	console.log(event.data);
}
function contactUsButtonHandler(eventObj){
	console.log("Event Received : " + event.type);
	console.log(event.data);
}
var customToolbarData = [];
customToolbarData.push({"id" :"help","config":{"position":"rear","imageUrl":"http://<path_of_the_image>/help.png","toolTip":"Help"},"handler":helpButtonHandler});
customToolbarData.push({"id" :"contactUs","config":{"toolTip":"Help","isPrimary":false},"handler":contactUsButtonHandler});

sessionObject.addToolbarBtns(customToolbarData);
```
### (inner) changeResolution(bounds)

Changes the resolution of the session.

#### Parameters

| Name | Type | Description |
|---|---|---|
| `bounds` | Object | Contains session resolution settings |

#### Properties

| Name | Type | Description |
|---|---|---|
| `bounds.autoresize` | boolean | 	Should be set to false to give fixed width and height to session. If this value is set to true then the session is resized to match the size of iframe element or the tab. |
| `bounds.width` | Number | Width of the session specified in pixels. This value will be set only when autoresize is set to false. |
| `bounds.height` |	Number | Height of the session specified in pixels. This value will be set only when autoresize is set to false. |

#### Examples

**Example 1:** To change resolution to fixed width and height

```
var bounds = {
	"autoresize":false,
	"width": "800",
	"height":"600"
}
sessionObject.changeResolution(bounds);
```

**Example 2:** To change the session resolution to match the iframe element or tab size

```
var bounds = {
	"autoresize": true
}
sessionObject.changeResolution(bounds);
```
### (inner) disconnect()

Disconnects the session.

### (inner) logoff()

Sends logoff to the session.

### (inner) removeListener(eventType, eventListener)

Removes the eventListener on the eventType.

#### Parameters

| Name | Type | Description |
|---|---|---|
| `eventType` | String | Type of the event for which the listener needs to be removed. Supported event types: <br> - [onConnection](./events#onconnection) <br> - [onConnectionClosed](./events#onconnectionclosed) <br> - [onURLRedirection](./events#onurlredirection) <br> - [onError](./events#onerror) |
| `eventListener` | [eventListener](./global#eventlistener) | Listener to handle the event |

#### Example

```
//Removing the event handler for onConnection event
function connectionHandler(eventObj){
	console.log("Event Received : " + event.type);
	console.log(event.data);
}
sessionObject.removeListener("onConnection",connectionHandler);
```

### (inner) removeToolbarBtns(toolbarButtonIds)

Removes the custom toolbar buttons added to in-session toolbar.

#### Parameters

| Name | Type	 | Description |
|---|---|---|
| `toolbarButtonIds` | Array &lt;String&gt; | Array of custom toolbar button ids to be removed. |

#### Example

**Example 1:** Removing the help button added using addToolbarBtns example.

```
sessionObject.removeToolbarBtns(["help"]);
```

**Example 2:** Removing multiple buttons say back and forward buttons added using addToolbarBtns example.

```
sessionObject.removeToolbarBtns(["back","forward"]);
```

### (inner) sendSpecialKeys(keys)

Sends a key combination to the session.

#### Parameters

| Name | Type | Description |
|---|---|---|
| `keys` | Array	| Array of strings with each one representing a key. Supported keys Alt, Control, Shift, ArrowDown, ArrowLeft, ArrowRight, ArrowUp, Home, End, PageUp, PageDown, Backspace, Delete, F5, PrintScreen,Insert, Escape, Tab. Till 1.1 version only "ctrl+alt+del" was supported. From 1.2 version, more key combinations can be sent to session. |

#### Example

**Example 1:** Sends Ctrl+alt+delete to the session.

```
var keys = ["Control","Alt","Delete"];
sessionObject.sendSpecialKeys(keys);
```

**Example 2:** To preview different apps running inside session, Ctrl+alt+tab can be sent.
```
var keys = ["Control","Alt","Tab"];
sessionObject.sendSpecialKeys(keys);
```

### (inner) start(launchData)

Starts the session.

#### Parameters

| Name | Type | Description |
|---|---|---|
| `launchData` | Object	 | Contains the type and value of ICA. |

#### Properties:

| Name | Type | Description |
|---|---|---|
| `launchData.type` | String | Specifies the data type of ICA data. Allowed values are "json" or "ini". |
| `launchData.value` | String | ICA data to start the session. It should be a JSON object when type is "json" or a string read from a .ini file when type is "ini". |

#### Examples

**Example 1:** When ICA data is in JSON format

```
var icaObj = {
	"ClientName":"HTML5-Receiver",
	"Domain":"<domain_name>",
	"ClearPassword":"<password>",
	"InitialProgram":"<initial program",
	"Title":"<title>",
	"Address":"<ip address>",
	"Username":"<user name>",
	"wsPort":"<port val>"
}
var launchData = {"type" : "json",value : icaObj};
sessionObject.start(launchData);
```

**Example 2:** When ICA data is in INI format

```
var launchData = {"type" :"ini",value :"<ica data in ini format>"};
sessionObject.start(launchData);			
```