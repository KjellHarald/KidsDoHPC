# KidsDoHPC

## Dashboard


## API

## Execute Python over API
The Kids Do HPC API allows Python Code to be executed on compute node(s).

```
import requests
code = "print(7 * 7)"

data = {'rpy': code}
r = requests.post('https://kidsdohpc.org/api/', data=data).text
```

### Code Examples
As the API recieves code as a string, it's very important to format this correctly. Unless rpy-file is used. When writing *code* as a string in python we need to utilize escaped characters.

```
code = "from os import system\nprint(system('whoami'))"
```

**Notice** the "\n" in the *code* above. This means "new line". In some cases an indent is also required. And this is when using *rpy-file* will become alot easier than *rpy*.

```
code = "for i in range(10):\n\ttprint(i)"
```

This will become the same as:

```
for i in range(10):
    print(i)
```

It's possible to utilize "\n" and "\t" as many times as is needed. So this is all you need to know to write Python code as a *string*.

### What is a "Compute Node"?
A "Compute Node" or simply *node* is one server that runs your program.
Kids Do HPC have serval *nodes*, what *node* your code is executed on is decided by the API.

### What happens on the Compute Node
When your code is sent over the API, each *node* have a small script that execute the code that it recieves. Very similar to if you would write "python3 file.py" to execute your Python code in your terminal.

### Empty Return
Empty API Returns are common if the API have *timeout*. A *timeout* happens because the code use too much time to execute and is terminated.

While *timeout* is the most common reason for *empty returns*, it's not the only reason.

- Code Error(s) and Code Spelling Mistakes.

## Outbound Security

**Guardian** ensure outbound security, by forcing outbound connections over an HTTP API.
That is routed over two diffirent NICs from Internal to External Connection. This also gives "network" connectivity to all compute nodes.

As Guardian can only communicate outbound traffic to HTTP/HTTPS Requests. They are easily filtered by protocool. And can be **strictly** byte forced.

Node -------> Controller (strict byte check) -----> E.g: https://wikipedia.org/

Guardian will return information from wikipedia.org **only** if byte check is validated. And wikipedia.org is a whitelisted resource.

Node <------- Controller <------------------- Result
