## Stomp Client [![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)
This project is a simple STOMP client in _Swift_,
and we use [_Starscream_](https://github.com/daltoniam/starscream) as a websocket dependency.

* Current version supports _Swift 3_.

### Usage
First thing is to import the _Starscream_ and _StompClient_ frameworks.
Once imported, you're able to connect to the server. Note that `client` is probably best as a property, so it doesn't get deallocated right after being setup.

    let url = server_url
    client = StompClient(url: url)
    client = self
    client.connect()

After you are connected, there are some delegate methods that you need to implement.

#### Delegate Methods
`stompClientDidConnected(client: StompClient)` is called when the client connects to the server.

`stompClient(client: StompClient, didErrorOccurred error: NSError)` is called when error occurs.

`stompClient(client: StompClient, didReceivedData data: NSData, fromDestination destination: String)` is called when the client receive a message from a subscription destination.

#### Subscription
You can use `subscribe(destination: String, parameters: [String : String]?)` method to subscribe a topic, and this method will return a destination id string.
Please pass this string to the second argument when invoking `unsubscribe(destination: String, destinationId: String)`

### Installed by Carthage
Add the following line into your _Cartfile_,

      github "ShengHuaWu/StompClient"

, and then run `carthage update --platform ios` in your terminal.
