# Open API

## Code as *file*

```python
import requests

data = {'rpy-file': open('/path/test.py', 'rb')}

api_call = requests.post('https://kidsdohpc.org/api/open/', files=data)
print(api_call.text)
```

## Code as *string*

```python
import requests

data = {'rpy': 'print(7 * 7)'}
r = requests.post('https://kidsdohpc.org/api/open/', data=data).text
print(r)
```