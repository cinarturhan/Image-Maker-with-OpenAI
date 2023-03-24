# Image-Maker-with-OpenAI
Using a prompt to create images.


```python
import os
import openai
import requests
from IPython.display import Image
from IPython.core.display import HTML 
from PIL import Image as pil_image
import numpy as np


openai.api_key = "YOUR KEY"
```


```python
prompt = input("Describe the image: ")

response = openai.Image.create(
  prompt=prompt,
  n=1,
  size="1024x1024"
)
image_url = response['data'][0]['url']


image_content = requests.get(image_url).content
Image(image_content)


with open("image3.png", "wb") as f:
    f.write(image_content)
    
Image(image_content, height=500, width=500)
```

    Describe the image: cats taking selfie on a roof with city view, digital art
    




    
![png](/output/output_1_1.png)
    



Masks:


```python
# response = openai.Image.create_edit(
#   image=open("image.png", "rb"),
#   mask=open("mask.png", "rb"),
#   prompt="A sunlit indoor lounge area with a pool containing a flamingo",
#   n=1,
#   size="1024x1024"
# )
# image_url = response['data'][0]['url']
```

Variation:


```python
response = openai.Image.create_variation(
  image=open("image.png", "rb"),
  n=1,
  size="1024x1024"
)
image_url = response['data'][0]['url']
image_content = requests.get(image_url).content
Image(image_content, height=300, width=300)
```




    
![png](/output/output_5_0.png)
    




```python
response = openai.Image.create_variation(
  image=open("image.png", "rb"),
  n=1,
  size="1024x1024"
)
image_url = response['data'][0]['url']
image_content = requests.get(image_url).content
Image(image_content, height=300, width=300)
```




    
![png](/output/output_6_0.png)
    




```python
response = openai.Image.create_variation(
  image=open("image.png", "rb"),
  n=1,
  size="1024x1024"
)
image_url = response['data'][0]['url']
image_content = requests.get(image_url).content
Image(image_content, height=300, width=300)
```




    
![png](/output/output_7_0.png)
    



---

---
