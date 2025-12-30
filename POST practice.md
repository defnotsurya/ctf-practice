# ctflearn- POST Practice (medium)
## Problem 
This website requires authentication, via POST. However, it seems as if someone has defaced our site. Maybe there is still some way to authenticate? http://165.227.106.113/post.php
Link - https://ctflearn.com/challenge/114
From the description, the challenge seems to be about making a POST request and geting the login information.

Going to the page it brings you this
<img width="764" height="57" alt="image" src="https://github.com/user-attachments/assets/a27cbf64-36a7-4cfd-8571-f4f53031ad7d" />

There is nothing else on the page, but looking at the source will give you the credentials for the login.
<img width="847" height="25" alt="image" src="https://github.com/user-attachments/assets/bff6f50c-af67-4985-af6d-f88703db2bb1" />

Now we know the values for each parameter, now need to send a request

## Python
I used python to send a request using the following
```python
import requests

url = "http://example.com"

response = requests.get(url)
print(response.text)
---
# Conclusion

This challenge demonstrates that authentication depends on backend request handling, not the frontend interface.
Even when a login page is defaced or removed, manually crafting HTTP POST requests can still allow authentication if the backend logic remains intact.

This was a straightforward challenge that reinforced how POST requests work and how Python can be used to interact with web applications.
