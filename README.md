# Map_Visualization
## 서울시 법정동 기준 지도 시각화


본 repository는 해당 [링크](https://github.com/raqoon886/Local_HangJeongDong/blob/master/README.md)를 참고했습니다.
 

____
용어설명. 
geojson: repository의 geojson파일, 해당 geojson은 [국가공간정보포털](http://data.nsdi.go.kr/dataset)의 데이터를 가공. 
locations: 데이터셋에서 geojson파일에 매칭시킬 컬럼. 
color: 시각화 할 컬럼. 
color_continuous_scale: [plotly 패키지](http://data.nsdi.go.kr/dataset)의 color scale. 
featureidkey: geojson에 매칭될 컬럼(해당 geojson에서는 properties.EMD_NM. 
mapbox_style: 지도레이어 박스 스타일. 
center: 중심점 (서울: 37.563383, 126.996039). 

```python
import os, json
import pandas as pd
import plotly.express as px

with open('/Users/ranking/OneDrive - UOS/석사2학기/seoul_beobjeongdong.geojson','r') as f:
    new_geo = json.load(f)

sample = pd.read_csv('https://raw.githubusercontent.com/hyeokkukim/Map_Visualization/main/sample.csv')

fig = px.choropleth_mapbox(sample, #데이터셋
                           geojson=new_geo, #geojson 파일
                           locations='gongsi_동리', #데이터에서 매칭시킬 컬럼 지정
                           color='diff', #volumne 컬럼
                           color_continuous_scale='RdPu', #color scale
                           featureidkey = 'properties.EMD_NM', #geojson에서 매칭시킬 컬럼 지정
                           mapbox_style='carto-positron',
                           zoom=9.5,
                           center = {"lat": 37.563383, "lon": 126.996039}, #중심점 = 서울
                           opacity=0.5,
                          )

fig
```
