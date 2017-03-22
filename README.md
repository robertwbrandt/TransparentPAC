# TransparentPAC
Transparent PAC file

The purpose of this project is to create a simple to configure and monitor squid proxy to act as a PAC file for transparent proxies.
The situation that necesitated this project is that we had a situation where we needed to use a certain type of proxy (Websense) to access the internet.  These proxies used WEB authentication to determine which URLs users were allowed to go.  As no devices I know of are capable of using WEB authentaction for Proxy authentication, we need a solution that allowed devices to pass to their resources directly but sent the remaining users to the downstream proxy. This solution will also allow us to use the proxies in a transparent configuration (where the firewall itself redirects all HTTP(S) traffic to the proxy.

The design is simple enough:
There is a single XML file which contains all the parameters and "rules" what are all very basic. 
These rules are defines with various actions (whitelest, blacklist, logging)
If a request is Blacklisted it is denied!
If a request is Whitelisted it is allow out directly.
All other requests are sent downstream to the next proxy (which will ask for authentication)

There will also be a logging component that will send a record of all requests to a MySQL server to future review.  And since this system will be unaware of which user is supplying each request, it will contain a system that will "Guess" the username based off Mail, Instant Messaging and Domain logins.
