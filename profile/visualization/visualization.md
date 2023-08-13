# Opensearch Kibana 시각화 하기 

## 1.Geolocation 설정 
![image](https://drive.google.com/uc?id=1HmQdPq3HwHEZnCCIipo8uf-7Ec0LrTBY)
>geo_location 설정을 위해 아래 코드를 Opensearch dev tools console에 입력해준다.
```
PUT ban_list{
 "mappings":{
    "properties":{
        "location":{
            "type": "geo_point"
        }
    }
 }
}
```

## 2.index pattern 생성
![image](https://drive.google.com/uc?id=1Z4VVwwVzI8fxjKHBNVPyD7CdgY88AT3D)
> OpenSearch Dashboard -> Index Patterns -> Create index pattern 


![image](https://drive.google.com/uc?id=1-mIHkxAp73T1sbbDbaR09uaEKih_4gX1)
> Time field는 timestamp로 설정후 생성

## 3.DashBoard 생성 
![image](https://drive.google.com/uc?id=1k-x8tMGpr5ktvij54VuPfWbR2leWFfkw)
>OpenSearch Dashboard -> Create new -> Line 선택 -> Choose a source는 ban_list로 설정후 생성

![image](https://drive.google.com/uc?id=1umCfIjr784imNll2-dTayKWzsS6PColW)
>생성후 크롤링된 기록이 그래프로 찍히게 된다.

## 4.Map 생성 
![image](https://drive.google.com/uc?id=1oq3NqpGNhQt4Gl0NJqfo3wk64CA7nzFV)
 >OpenSearch -> Maps -> Create map -> Add layer -> Documents

![image](https://drive.google.com/uc?id=1PlrEpzzRk_Sb3i5_wXbNzqm5G8lJSPAT)
>Data source는 ban_list Geopatial field는 location Number of documents는 1000으로 설정하고 Update

![image](https://drive.google.com/uc?id=13DQ-U9A9joA6_-7TlDvDYGMImvhURxG0)
> Style 설정을 통해 잘보이게 Fill color 와 Border color 을 red로 설정하면 아래 그림에서 어디서 크롤링이 됐는지 지도를 통해 확인 할수있다.

