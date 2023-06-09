# export-Android-Chrome-open-tabs
get a JSON list of all currently open tabs from your android device

[Reference](https://android.stackexchange.com/a/199496)


[Install Android command line tools on PC](https://developer.android.com/studio/#downloads)

Enable USB debugging on Android device

On the PC execute 
` adb forward tcp:9222 localabstract:chrome_devtools_remote ` 

Chrome instances expose access to a debugging protocol via a unix domain socket with the abstract address "chrome_devtools_remote" 

[Read about abstract namespaces and addresses](https://utcc.utoronto.ca/~cks/space/blog/linux/SocketAbstractNamespace)

Executing the adb command listed above will forward requests to port 9222, on to that socket. 

You can get a list of all the unix domain sockets on the Android device by typing 
` adb shell cat /proc/net/unix `

The debugging protocol exposes JSON data about the chrome instance over HTTP. 

A JSON file listing the open tabs can be retrieved by executing 
` wget -O tabs.json http://localhost:9222/json/list `

[View all endpoints of the API](https://github.com/buggerjs/bugger-daemon/blob/master/README.md#api)

[Enabling USB debugging](https://developer.chrome.com/devtools/docs/remote-debugging-legacy)

[Overview of remote debugging in Chrome](https://www.girish.in/how-remote-debugging-works-in-chrome/)


[lmmx's wiki for android-open-tabs-export via chrome debug console](https://github.com/lmmx/devnotes/wiki/Export-all-Chrome-tabs-on-Android)

