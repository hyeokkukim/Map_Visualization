# Map_Visualization
지도 시각화




# 참고: https://github.com/raqoon886/Local_HangJeongDong/blob/master/README.md
# shp -> json: https://park9eon.com/how-to-convert-to-korea-shp-geojson/

'''python
import os, json
import pandas as pd
import plotly.express as px

with open('/Users/ranking/OneDrive - UOS/석사2학기/seoul_beobjeongdong.geojson','r') as f:
    new_geo = json.load(f)

dong_data = pd.DataFrame(df[df['apt_기준연도'] == 2021].groupby('gongsi_동리')['diff'].mean()).reset_index()
dong_data['diff'] = dong_data['diff'] / dong_data['diff'].max()

fig = px.choropleth_mapbox(dong_data, #데이터셋
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
'''
