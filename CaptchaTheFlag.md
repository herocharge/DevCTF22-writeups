## Captcha The Flag

This is my proudest solve.  
The target was pretty straightforward.

I needed to enter captcha displayed in the website as an image (it had like 12 characters in each image).  
I had to enter the captcha in 3 secs which is humanly not possible.  

AUTOMATION TIME!!

I quickly wrote a python script to GET the website and extract the image information using `requests` and `bs4`.

```python

import requests
from bs4 import BeautifulSoup
r = requests.get('https://web.ctf.devclub.in/dev/4/')
h = BeautifulSoup(r.text)
val = h.body.find('input')['value']
img64 = h.body.find('img')['src'][24:]

```
I noticed that the image was give in base64 format and not a link to an JPG/PNG image. So I used the `PIL` library to convert it to an image and store it locally.

```python

from PIL import Image
import base64

with open("cap.jpeg", "wb") as fh:
    fh.write(base64.decodebytes(bytes(img64, 'ascii')))

```

Now it's time for some OCR magic. I used `pytesseract` to extract the string from the image.

```python

import pytesseract

ans = (pytesseract.image_to_string("cap.jpeg")).strip()

```

Then it was just a simple post request away from the solution

```python

payload = [('tt', val), ('captcha', ans)]
r = requests.post('https://web.ctf.devclub.in/dev/4/', data=payload)
print(r.text)

```
