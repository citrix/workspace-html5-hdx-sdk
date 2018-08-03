## Session Launch

Currently Workspace app for Web launches the HTML5 HDX session in a new tab. This API allows HTML5 HDX session to be embedded within a website or to be opened in a new tab.

## Workspace app for HTML5 app Events

HTML5 HDX session provides a set of events for the website to give better control on the session with respect to various connection states, errors and URL redirection. The user experience with the HDX session can be customized using the events.

## UI Customizations

It is possible to leverage the embedding of the session along with the Workspace app events to achieve some of the UI customizations mentioned below to build preferred experience:

1. Session connection experience
>- Custom connection experience could be built using the various connection events.

2. Error dialog customization
>- Suppress error dialog shown by Workspace app for HTML5 and show the custom error dialog: When the session is embedded within the website, custom error UI that aligns with the website could be shown using the error events and suppressing the error dialog shown by Workspace app for HTML5 using the configuration options.
>- Error dialog shown by Workspace app for HTML5 with custom error message: Error messages in the locales folder can be edited which will be picked by error dialog shown by Workspace app for HTML5.
>- URL Redirection dialog customization URL redirection can be customized by the website using the urlredirection events and suppressing the URL redirection dialog shown by Workspace app for HTML5 using the configuration options.
>- Session close UI customization Action on disconnecting the session can be customized using the API params, so that session can be closed with/without prompting user. Also web site can be configured to redirect to a specified URL after session close

## Session Operations
>- Change active session resolution API allows the session resolution to be changed dynamically
>- Send key combinations to session More useful special key combinations can be sent to the active session. For 1example, Ctrl+Alt+Del, F5 , Home, end etc…
>- Add/remove custom toolbar buttons Custom toolbar buttons can be added/removed as primary/secondary menu items to an active session

## Session disconnect

Website could disconnect to the session using this API. This is more helpful when the in-session toolbar is hidden.