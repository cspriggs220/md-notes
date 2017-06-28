Testing on IE using npm's iectrl

- Find out your current IP addy via Sys Prefs<Network
- Make sure the rails server is running using:
```rails s -b 0.0.0.0```
- Start iectrl with the IE version followed by the url
```iectrl open -s 9 http://{current_IP}:3000/elp/sell-my-house```


## More info
Binding to 0.0.0.0 tells the service to bind to all IP addresses on your machine. Rails server used to do this by default, but with 4.2 changed to binding only to localhost.

Basically if it's only bound to localhost then it will only respond locally to either localhost or 127.0.0.1 which can't work through a DNS service because it's not a public IP address.

When you use 0.0.0.0 it will bind to localhost and to your routable IP address.
