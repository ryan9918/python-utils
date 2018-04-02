# Python Utils
Two python classes that I use as a base for all my projects

## Requirements
- `python 3+`
- `colorama`
- `termcolor`

## Usage
Importing and initialising the classes
```
from utils import Logger, ProxyManager

logger = Logger()
proxymanager = ProxyManager()
```
### Logger
- `logger.log("did something")`: produces normal output with a timestamp
- `logger.success("did something good")`: produces green output with a timestamp
- `logger.error("did something bad")`: produces red output with a timestamp
- `logger.warn("did something not so good")`: produces yellow output with a timestamp
- `logger.status("about to do something")`: produces purple output with a timestamp
### ProxyManager
The system works by returning the proxy from the top of the list and then moving it to the bottom. That way it rotates through proxies.
`proxymanager.get_proxy()`
Returns a proxy in the necessary format for usage in a request

## Example
```
import requests
from utils import Logger, ProxyManager

logger = Logger()
proxymanager = ProxyManager()

logger.log("Sending http request")
r = requests.get('https://example.org', proxy=proxymanager.get_proxy())
if r.status_code == 200:
  logger.success("OK response received")
else:
  logger.error("Something bad happened")
```

## Help
You shouldn't need it.
