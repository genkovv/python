```python
import pandas as pd
import numpy as np
from pandas import ExcelWriter
from pandas import ExcelFile
```


```python
df = pd.read_excel('platform-test.xlsx')
```


```python

df.head(7)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>car</th>
      <th>model</th>
      <th>colour</th>
      <th>country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Audi</td>
      <td>80</td>
      <td>red</td>
      <td>Canada</td>
    </tr>
    <tr>
      <th>1</th>
      <td>BMW</td>
      <td>320d</td>
      <td>blue</td>
      <td>Brunei</td>
    </tr>
    <tr>
      <th>2</th>
      <td>BMW</td>
      <td>530e</td>
      <td>Amaranth</td>
      <td>Bulgaria</td>
    </tr>
    <tr>
      <th>3</th>
      <td>BMW</td>
      <td>218i</td>
      <td>Amber</td>
      <td>Ecuador</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jaguar</td>
      <td>F-Pace</td>
      <td>Amethyst</td>
      <td>East Timor</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Moskvich</td>
      <td>8-ca</td>
      <td>Apricot</td>
      <td>Ecuador</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Moskvich</td>
      <td>12-ka</td>
      <td>Aquamarine</td>
      <td>Egypt</td>
    </tr>
  </tbody>
</table>
</div>




```python
df=df.sort_values(by="car", ascending=True)
df=df.reset_index(drop=True)
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>car</th>
      <th>model</th>
      <th>colour</th>
      <th>country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Aston-Martin</td>
      <td>NaN</td>
      <td>Blue</td>
      <td>San Marino</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Audi</td>
      <td>80</td>
      <td>red</td>
      <td>Canada</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Audi</td>
      <td>S8</td>
      <td>Blue-green</td>
      <td>Sao Tome and Principe</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Audi</td>
      <td>Q7</td>
      <td>Cerise</td>
      <td>Mauritania</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Audi</td>
      <td>S3</td>
      <td>Carmine</td>
      <td>Marshall Islands</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[["model"]]=df[["model"]].astype(str)
i=1
m=0
for i in range(0,df.shape[0]):
    if  df.iloc[i,0] == df.iloc[i-1,0]:
        df.iloc[i,1] = df.iloc[i-1,1]+df.iloc[i,1]+"\\\\"
        df.iloc[i-1,1] = df.iloc[i,1]
        m=m+1
        if (m > 1):
            for n in range(1,m+1):
                  df.iloc[i-n,1] = df.iloc[i,1]
    else:
        df.iloc[i,1] = df.iloc[i,1]+"\\\\"
        m=0            
```


```python
#df[["model"]]=df[["model"]].astype(object)
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>car</th>
      <th>model</th>
      <th>colour</th>
      <th>country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Aston-Martin</td>
      <td>nan\\</td>
      <td>Blue</td>
      <td>San Marino</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Audi</td>
      <td>80\\S8\\Q7\\S3\\A3\\A6\\90\\A4\\</td>
      <td>red</td>
      <td>Canada</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Audi</td>
      <td>80\\S8\\Q7\\S3\\A3\\A6\\90\\A4\\</td>
      <td>Blue-green</td>
      <td>Sao Tome and Principe</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Audi</td>
      <td>80\\S8\\Q7\\S3\\A3\\A6\\90\\A4\\</td>
      <td>Cerise</td>
      <td>Mauritania</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Audi</td>
      <td>80\\S8\\Q7\\S3\\A3\\A6\\90\\A4\\</td>
      <td>Carmine</td>
      <td>Marshall Islands</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Audi</td>
      <td>80\\S8\\Q7\\S3\\A3\\A6\\90\\A4\\</td>
      <td>Byzantium</td>
      <td>Malta</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Audi</td>
      <td>80\\S8\\Q7\\S3\\A3\\A6\\90\\A4\\</td>
      <td>Brown</td>
      <td>Maldives</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Audi</td>
      <td>80\\S8\\Q7\\S3\\A3\\A6\\90\\A4\\</td>
      <td>Bronze</td>
      <td>Malaysia</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Audi</td>
      <td>80\\S8\\Q7\\S3\\A3\\A6\\90\\A4\\</td>
      <td>Burgundy</td>
      <td>Mali</td>
    </tr>
    <tr>
      <th>9</th>
      <td>BMW</td>
      <td>8i\\320d\\530e\\218i\\</td>
      <td>Blue-violet</td>
      <td>Saudi Arabia</td>
    </tr>
    <tr>
      <th>10</th>
      <td>BMW</td>
      <td>8i\\320d\\530e\\218i\\</td>
      <td>blue</td>
      <td>Brunei</td>
    </tr>
    <tr>
      <th>11</th>
      <td>BMW</td>
      <td>8i\\320d\\530e\\218i\\</td>
      <td>Amaranth</td>
      <td>Bulgaria</td>
    </tr>
    <tr>
      <th>12</th>
      <td>BMW</td>
      <td>8i\\320d\\530e\\218i\\</td>
      <td>Amber</td>
      <td>Ecuador</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Bugatti</td>
      <td>Cool\\</td>
      <td>Blush</td>
      <td>Senegal</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Cadillac</td>
      <td>Elvis\\</td>
      <td>Bronze</td>
      <td>Serbia</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Chevrolet</td>
      <td>Trailblazer\\</td>
      <td>Brown</td>
      <td>Seychelles</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Dodge</td>
      <td>Carger\\</td>
      <td>Burgundy</td>
      <td>Sierra Leone</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Ferrari</td>
      <td>nan\\</td>
      <td>Byzantium</td>
      <td>Singapore</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Ford</td>
      <td>nan\\</td>
      <td>Blue</td>
      <td>Ethiopia</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Jaguar</td>
      <td>F-Pace\\</td>
      <td>Amethyst</td>
      <td>East Timor</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Lada</td>
      <td>Jiguli\\Niva\\</td>
      <td>Beige</td>
      <td>Eritrea</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Lada</td>
      <td>Jiguli\\Niva\\</td>
      <td>Black</td>
      <td>Estonia</td>
    </tr>
    <tr>
      <th>22</th>
      <td>Mercedes</td>
      <td>E320\\A180\\S500\\SLK\\SLS\\C240\\</td>
      <td>Cerulean</td>
      <td>Mauritius</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Mercedes</td>
      <td>E320\\A180\\S500\\SLK\\SLS\\C240\\</td>
      <td>Chartreuse green</td>
      <td>Micronesia, Federated States of</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Mercedes</td>
      <td>E320\\A180\\S500\\SLK\\SLS\\C240\\</td>
      <td>Chocolate</td>
      <td>Moldova</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Mercedes</td>
      <td>E320\\A180\\S500\\SLK\\SLS\\C240\\</td>
      <td>Cobalt blue</td>
      <td>Monaco</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Mercedes</td>
      <td>E320\\A180\\S500\\SLK\\SLS\\C240\\</td>
      <td>Coffee</td>
      <td>Mongolia</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Mercedes</td>
      <td>E320\\A180\\S500\\SLK\\SLS\\C240\\</td>
      <td>Champagne</td>
      <td>Mexico</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Moskvich</td>
      <td>408\\12-ka\\412\\8-ca\\</td>
      <td>Baby blue</td>
      <td>Equatorial Guinea</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Moskvich</td>
      <td>408\\12-ka\\412\\8-ca\\</td>
      <td>Aquamarine</td>
      <td>Egypt</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Moskvich</td>
      <td>408\\12-ka\\412\\8-ca\\</td>
      <td>Azure</td>
      <td>El Salvador</td>
    </tr>
    <tr>
      <th>31</th>
      <td>Moskvich</td>
      <td>408\\12-ka\\412\\8-ca\\</td>
      <td>Apricot</td>
      <td>Ecuador</td>
    </tr>
    <tr>
      <th>32</th>
      <td>Tata</td>
      <td>nan\\</td>
      <td>Black</td>
      <td>Samoa</td>
    </tr>
    <tr>
      <th>33</th>
      <td>WV</td>
      <td>Golf\\Passat\\Polo\\</td>
      <td>Blush</td>
      <td>Malawi</td>
    </tr>
    <tr>
      <th>34</th>
      <td>WV</td>
      <td>Golf\\Passat\\Polo\\</td>
      <td>Blue-violet</td>
      <td>Madagascar</td>
    </tr>
    <tr>
      <th>35</th>
      <td>WV</td>
      <td>Golf\\Passat\\Polo\\</td>
      <td>Blue-green</td>
      <td>Macedonia</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
