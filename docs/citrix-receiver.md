# Namespace: receiver


##receiver
citrix.receiver


## Members 
<span class="type-signature">(readonly) </span>`apiVersion`<span class="type-signature"></span> 

###Properties:

  Name          | Type                                   | Description
  --------------|----------------------------------------|-----------------------------
  `apiVersion`  | <span class="param-type">String</span> | Workspace app for HTML5 API version.

## Methods
<span class="type-signature">(static) </span>createSession<span class="signature">(id<span class="signature-attributes">opt</span>, connectionParams, onSessionCreated)</span><span class="type-signature"></span>

Creates a new session and returns session instance through callback. Use session instance to start the session, register and handle events and to disconnect the session.

#### Parameters

| Name | Type | Attributes | Description |
|---|---|---|---|
| `id` | string | &lt;optional&gt; | ID that is assigned when the session is created |
| `connectionParams`	 | [connectionParams](./global#connectionparams) | | Configuration options to create the session |
| `onSessionCreated` | [onSessionCreated](./global#onsessioncreated) | | Callback containing the session object created. Signature sample below: <br> `function <function_name>(session_object){...}` | 

#### Throws:
Unable to create session object.

Type   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="param-type">[ReceiverError](/ReceiverError)</span>

#### Example

Following code launches an app/desktop in an iframe. Setting preferences to hide the in-session toolbar.

````js
try{
    citrix.receiver.setPath("http://html5client_hosted_url/");
    var id = "session1"; //Optional parameter
    var connectionParams = {
            "launchType" : "embed",
            "container" : {
                "type" : "iframe",
                "value" : "sessionIframe"
            },
            "preferences" : {
                "ui" : {
                    "toolbar" : {
                        "menubar" : false
                    }
                }
            }
        };
    function sessionCreated(sessionObject){
        
        //Handle session interactions like events, start, disconnect here.              
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
    citrix.receiver.createSession(id,connectionParams,sessionCreated);
}catch(ex){
    console.log(ex);
}
````

## Methods  
<span class="type-signature">(static) </span>setPath<span class="signature">(path)</span><span class="type-signature"></span> {#.setPath .name}

Sets the HTML5Engine Path. Must be set before creating a session.  

#### Parameters:

  Name    | Type                                    | Description
  --------| ----------------------------------------| -----------------------------
  `path`  | <span class="param-type">string</span>  | Path of HTML5Client folder.
  
#### Throws:
    Path is empty.


Type   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="param-type">[ReceiverError](/ReceiverError)</span>
  
<span class="type-signature">(static) </span>viewLog<span class="signature">()</span><span class="type-signature"></span> {#.viewLog .name}


Opens the logging page in a new tab.HTML5Engine Path should be set
before calling this API.

  
#### Throws:
HTML5 Engine Path is not set.

Type  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="param-type">[ReceiverError](/ReceiverError)</span>


