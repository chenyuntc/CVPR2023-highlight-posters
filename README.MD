# posters for all CVPR2023 Highlight papers

# [Poster for CVPR 2024 Award Papers](https://github.com/chenyuntc/CVPR2024-award-posters)


## script used to download
```python
import requests
from bs4 import BeautifulSoup

url = 'https://cvpr.thecvf.com/virtual/2023/awards_detail'
response = requests.get(url)
soup = BeautifulSoup(response.text, "html.parser")

id2title = dict() 
for link in soup.find_all('a'):
    if link.get('href').startswith('/virtual/2023/poster/'):
        paper_id = (link.get('href').split('/')[-1])
        id2title[paper_id] = link.get_text()


for paper_id, title in id2title.items():
    url = f"https://cvpr.thecvf.com/media/PosterPDFs/CVPR%202023/{paper_id}.png"
    title = title.replace(' ','_').replace(':','-').replace('\\','').replace('/','')
    save_path = f"{paper_id}_{title}_poster.png"
    get_ipython().system('wget $url -O $save_path')
```

![Unisim](posters/22272_UniSim-_A_Neural_Closed-Loop_Sensor_Simulator_poster.png)



