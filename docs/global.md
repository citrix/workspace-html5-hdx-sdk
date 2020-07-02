#Global


## Type Definitions

### <a name="connectionparams"></a>connectionParams

Configuration options to create the session.

#### Type

>-   <span class="param-type">Object</span>

#### Properties:
<table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>connectionParams</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="description last"> <h6>Properties</h6><table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th>Attributes</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>launchType</code></td><td class="type"> <span class="param-type">String</span> </td><td class="attributes"> &lt;optional&gt;<br></td><td class="description last">Takes "newtab" or "embed" as value. Defaults to "newtab". <br><br>"newtab" - launches the session in a new tab.<br>"embed" - Opens the session in an Iframe.</td></tr><tr> <td class="name"><code>container</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="attributes"> </td><td class="description last">Specifies the ID and the type of container for the session when launchType is embed. <br><h6>Properties</h6><table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>id</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">ID of the iframe element to embed the session. Mandatory parameter when launchType is embed.</td></tr><tr> <td class="name"><code>type</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Type of the element to embed the session. Should be set to "iframe".</td></tr></tbody></table> </td></tr><tr> <td class="name"><code>bounds</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="attributes"> &lt;optional&gt;<br></td><td class="description last">Sets a fixed width and height to the session. <h6>Properties</h6><table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>autoresize</code></td><td class="type"> <span class="param-type">boolean</span> </td><td class="description last">Should be set to false to give fixed width and height to session. By default, this value is set to true in which case the session is resized to match the size of iframe element or the tab.</td></tr><tr> <td class="name"><code>width</code></td><td class="type"> <span class="param-type">Number</span> </td><td class="description last">Width of the session specified in pixels. This value will be set only when autoresize is set to false.</td></tr><tr> <td class="name"><code>height</code></td><td class="type"> <span class="param-type">Number</span> </td><td class="description last">Height of the session specified in pixels. This value will be set only when autoresize is set to false.</td></tr></tbody></table> </td></tr><tr> <td class="name"><code>closeOptions</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="attributes"> &lt;optional&gt;<br></td><td class="description last">Action on disconnecting the session. Defaults to type="close". <h6>Properties</h6><table class="props"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>type</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Specifies the type of action.<br>type=”redirectUrl” would redirect the tab to the URL specified in value.<br>type=”close” would set the iframe src to "about:blank" when launchType is "embed" and closes the tab when launchType is "newtab".</td></tr><tr> <td class="name"><code>value</code></td><td class="type"> <span class="param-type">String</span> </td><td class="description last">Specifies the URL to be redirected. When type is set to "close",this value would be ignored.</td></tr><tr> <td class="name"><code>showDisconnectAlert</code></td><td class="type"> <span class="param-type">boolean</span> </td><td class="description last">A prompt would be shown to the user to stay/leave the current page when the session is about to disconnect due to the actions like close/reload of the tab. <br><br>If the value is set to true then the prompt is displayed otherwise prompt won't be shown. <br><br>Default value is true.</td></tr></tbody></table> </td></tr><tr> <td class="name"><code>preferredLang</code></td><td class="type"> <span class="param-type">String</span> </td><td class="attributes"> &lt;optional&gt;<br></td><td class="description last">Specifies the preferred language code to be used inside the session. If the language code specified is either invalid or unsupported then it falls back to "en". <br><br>Supported language codes : en, de, es, fr, ja, ko, ru, zh, zh-cn, zh-tw <br><br>If the value is unspecified then the browser's language code is used.</td></tr><tr> <td class="name"><code>preferences</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="attributes"> &lt;optional&gt;<br></td><td class="description last">JSON to hide/show toolbar or individual toolbar items, suppressing the FTU, URLRedirection and error dialog.<br>Refer to the example below.</td></tr></tbody></table> </td></tr></tbody></table>
#### Example

```java
connectionParams full example
{
    "launchType" : "embed",
    "container" : {
        "id" : "<iframe id>",
        "type" : "iframe"
    },
    "bounds" :{
        "autoresize":false,
        "width": "800",
        "height":"600"
    },  
    "closeOptions" : {
        "type" : "redirecturl",
        "value": "<url to redirect>",
        "showDisconnectAlert" : true //false won't prompt when the session is about to disconnect due to the actions like close/reload of the tab.
    },
    "preferredLang" : "ja", //Setting to Japanese
    "preferences" : {
        "ui" : {
            'toolbar' : {
                "menubar":true, //false - hides the toolbar
                "clipboard":true, //false - hides the clipboard button from toolbar         
                "fileTransfer":true, //false - hides the file upload and download buttons from toolbar
                "about":true, //false - hides the about button from toolbar
                "lock":true, //false - hides the ctrl+alt+del button from toolbar
                "disconnect":true, //false - hides the disconnect button from toolbar
                "logoff":true, // false - hides the logoff button from toolbar
                "fullscreen":true, //false - hides the fullscreen button from toolbar
                "keyboard":true, //false - hides the keyboard button from toolbar, this button appears only in touch devices
                "multitouch":true, //false - hides the multitouch button from toolbar, this button appears only in touch devices
                "switchApp":true, //false - hides the switchApp button from toolbar, this button appears only for apps session
                "preferences":true, //false - hides the preferences button from toolbar
                "gestureGuide":true //false - hides the gestureGuide button from toolbar, this button appears only in touch devices
            },
            "hide":{
                "urlredirection" : false, //true - hides the urlredirection dialog shown by HTML5 Engine
                "error" : false, //true - hides the error dialog shown by HTML5 Engine
                "ftu" : false //true - hides the FTU(first time user dialog) shown by HTML5 Engine
            },
            "appSwitcher": {
                "showTaskbar": true, //false - disables the desktop appSwitcher/taskbar seen at the bottom 
                "autoHide": false, //true - selects the Auto Hide checkbox present in the context menu of desktop appSwitcher/taskbar at the bottom  
                "showIconsOnly": false //true - selects the Show Icons only checkbox present in the context menu of desktop appSwitcher/taskbar at the bottom  
            }
        }
    }
}
```
  
### <a name="eventlistener"> eventListener(event) </a>

Listener to handle the events.

#### Parameters
  
<table class="params"> <thead> <tr> <th>Name</th> <th>Type</th> <th class="last">Description</th> </tr></thead> <tbody> <tr> <td class="name"><code>event</code></td><td class="type"> <span class="param-type">Object</span> </td><td class="description last">Object as appropriate to the eventType registered.</td></tr></tbody></table>

#### Properties

| Name | Type | Description |
|---|---|---|
| `event.id` | String | Id of the session object. |
| `event.type` | String | Event Type triggered. |
| `event.data` | Object | Data as appropriate to the event triggered. <br> - [onConnection](../events#onconnection) <br> - [onConnectionClosed](../events#onconnectionclosed) <br> - [onURLRedirection](../events#onurlredirection) <br> - [onError](../events#onerror) <br> - [onResize](../events#onresize) |

### <a name="onsessioncreated"></a>onSessionCreated(sessionObject)

Callback having the session object created.

#### Parameters

| Name | Type | Description |
|---|---|---|
| `sessionObject` | [Session](../session) | Session object to interact with the session like register and handle events, start and disconnect. |

#### Example

```javascript
function sessionCreated(sessionObject){
    //Handle session interactions like events, start, disconnect here.  
    //ICADATA has been constructed for example. Recommending to use StoreFront/WebInterface SDK to get ICA. 
    //Refer session.start() for more details.
    var icaData = {
        "Domain":"abcd",
        "ClearPassword":"xxxxxxxxx",
        "InitialProgram":"#Desktop",
        "Title":"Desktop",
        "Address":"xx.xx.xx.xx",
        "Username":"xyz"                
    };
    var launchData = {"type" :"json",value :icaData};
    sessionObject.start(launchData);
}
```
