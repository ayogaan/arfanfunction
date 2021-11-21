---
title: "Penerapan Multiple Linear Regression dalam Bahasa Pemrograman Python"
date: 2019-10-29T10:07:47+06:00
draft: false

# post thumb
image: "images/post/post-5.jpg"

# meta description
description: "this is meta description"

# taxonomies
categories: 
  - "Go Language"
tags:
  - "Photos"
  - "Game"
  - "HTML"
  - "Python"
  - "New"

# post type
type: "post"
---
hai teman teman, disini saya akan membagikan tutorial dalam bidang statistik yaitu linear regression, lebih tepatnya pengaplikasian multiple regression dalam bahasa pemrograman python.

apa tuh multiple regression trus bedanya sama simple linnear regression, trus gimana penerapanya ??
Linear regression adalah metode untuk ,emodelkan hubungan variable dependen dengan variable independen, dengan model tersebut nantinya kita dapat memprediksi nilai dari variable dependen nya jika diketahui variable independenya, begitu pula sebaliknya.

##### terus apa bedanya dengan multiple linear regression??


Secara matematis, persamaan dari Multiple Linear Regression / Regresi Linear Berganda adalah sebagai berikut:
  ```
  Y = b + e + m1*x1 + m2*x2 + … + mn*xn
  ```

  * Y = dependent variable
  * mn = koefisien dari persamaan
  * xn = independent variable
  * b = intercept
  * e = error 

##### menulis program di python
* pertama import dulu library yang dibutuhkan

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split
```
* selanjutnya kita import dataset yang kita miliki, disini saya menggunakan dataset biaya asuransi kesehatan yang saya dapatkan dari website kaggle.

* disini kita hanya akan mengambil kolom bmi, smoker dan charge

```
insurance_data = pd.read_csv('/home/arfan/Downloads/insurance.csv', usecols=['bmi','smoker','charges'])

```
* lalu untuk melihat sebagian data kita dapat menggunakan method head yang ada di library pandas, caranya

```
insurance_data.head()
```

* method ini akan mengembalikan nilai 5 kolom teratas dari dataset yang kita miliki, disini dapat kita lihat bahwa kolom smoker memiliki value berupa string yes dan no, sebelum melakukan regresi kita harus mengubah nilai tersebut ke integer, untuk mengubahnya kita bisa melakukan

```
insurance_data.smoker = pd.Series(np.where(insurance_data.smoker.values == 'yes', 1, 0), insurance_data.index)
insurance_data.head()
```

* sekarang nilai yes dan no pada kolom smoker telah diubah menjadi 0 dan 1, selanjutnya kita akan mengecek apakah dataset kita dapat dimodelkan dengan multiple regression, kita akan melihat hubungan antara dependen variable dengan variable independen nya.

```
plt.figure(figsize=(10,8))
sns.pairplot(data=insurance_data, x_vars=['bmi','smoker'], y_vars=['charges'], size=5, aspect=0.75)
```
* dari grafik yang dihasilkan terlihat bahwa nilai bmi dan smoker berpengaruh dengan nilai charge dimana perokok memiliki biaya perawatan kesehatan lebih tinggi dan pemilik bmi tinggi cenderung memiliki nilai charge yang tinggi pula. setelah itu kita dapat memodelkan dataset dengan multiple linear regression

```
x = insurance_data.drop(columns='charges')
y = insurance_data['charges']
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.2, random_state=4)
lin_reg = LinearRegression()
lin_reg.fit(x_train, y_train)
lin_reg.score(x_test, y_test)
```

* dari hasil diatas kita mendapati bahwa akurasi dari model yang kita peroleh adalah 61% hal ini cukup bagus untuk iterasi pertama mengingat kita tidak melakukan iterasi dan adanya outliners di data bmi.

lalu untuk mengecek biaya perawatan kesehatan kita dapat menjalankan kode
```
lin_reg.predict([[19.5,1]])
```

dimana parameter berisi array dengan value nilai bmi dan nilai smoker

pada artikel selanjutnya kita akan membuat halaman website untuk model yang kita buat, jadi stay tune