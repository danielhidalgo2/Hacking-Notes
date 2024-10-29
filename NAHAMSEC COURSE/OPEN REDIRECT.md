

Si encontramos una web que tiene un redirect, pero tiene una white list, una forma de bypassearlo es con "@"
```
https://example.com/?redirect=http://www.google.com@evil.com
```

En este caso ignorara google.com y se dirigirá a evil.com


OTRO BYPASS con /x//

```
https://auth.magnesium.ctfio.com/auth?client_id=1&redirect_url=https://magnesium.ctfio.com/x//evil.com&response_type=token
```