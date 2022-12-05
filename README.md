# KidsDoHPC

## Dashboard


## API


## Outbound Security

**Guardian** ensure outbound security, by forcing outbound connections over an HTTP API.
That is routed over two diffirent NICs from Internal to External Connection. This also gives "network" connectivity to all compute nodes.

As Guardian can only communicate outbound traffic to HTTP/HTTPS Requests. They are easily filtered by protocool. And can be **strictly** byte forced.

Node -------> Controller (strict byte check) -----> E.g: https://wikipedia.org/

Guardian will return information from wikipedia.org **only** if byte check is validated. And wikipedia.org is a whitelisted resource.

Node <------- Controller <------------------- Result