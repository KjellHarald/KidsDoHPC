# KidsDoHPC

## API

## Outbound Security

**Guardian** ensure outbound security by forcing outbound connections over an HTTP API.
That is routed over two diffirent NIC from Internal & External Connection. This also gives "network" connectivity to all compute nodes.

As Guardian can only communicate outbound traffic to HTTP/HTTPS Requests. They are easily filtered by protocool. And can be **strictly** byte forced.