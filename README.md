# TREduData

`Türkiye Education Data`

<p align="center">
[ENGLISH] <img src="https://github.com/jackiboy/flagpack/blob/master/flags/4x3/gb.svg" width="16" height="12">
</p>

This file is specifically prepared for data visualization, especially with maps. The data in the datasets are obtained from the official websites of government institutions and organizations. The datasets can be combined with Turkey level-1 (provinces) data, which can be freely downloaded from gadm.org, through a variable in these datasets (gadm_L3number), and then data visualization can be performed. An example R command line and the output obtained with this command are provided below.

```
library(sf)
library(dplyr)
library(ggplot2)

TR1 <- read_sf("C:/Your_Directory/gadm41_TUR_1.shp")
TR_coord <- st_coordinates(TR1)

TR_coord <- fortify(as_tibble(TR_coord))
TREduData_university <- read.csv("https://raw.githubusercontent.com/gungorMetehan/TREduData/main/TREduData_university.csv")

TR_Data <- TR_coord %>%
  full_join(x =., y = TREduData_university, by = c("L3" = "gadm_L3number"))

TR_Data %>% ggplot(aes(x = X, y = Y, group = L3, fill = num_totaluni_2023)) +
  geom_polygon() +
  coord_fixed() +
  theme_void() +
  scale_fill_viridis_c(option = "H") +
  guides(fill = guide_legend("Number of Universities")) +
  theme(legend.position = "bottom")
```
![Rplot01](https://github.com/gungorMetehan/TREduData/assets/102655648/67ce379f-aefb-4a82-8e39-865e8ad8b79e)

This file includes the following datasets:
1) TREduData_class: Contains data on classrooms in primary and secondary schools in provinces.
2) TREduData_exam: Contains data on various exams in Turkey.
3) TREduData_literacy: Contains data on literacy by provinces.
4) TREduData_school: Contains data on primary and secondary schools in provinces.
5) TREduData_student: Contains data on students in primary and secondary schools in provinces.
6) TREduData_teacher: Contains data on teachers in primary and secondary schools in provinces.
7) TREduData_university: Contains data on universities in provinces.

Codes in Variable Names
| Code             | English                  | Turkish              |
| ---------------- | ------------------------ | -------------------- |
| m                | Male                     | Erkek                |
| f                | Female                   | Kadın                |
| num              | Number                   | Sayı / Sayısı        |
| stu              | Student                  | Öğrenci              |
| pre              | Preschool                | Okul Öncesi          |
| ele              | Elementary               | İlkokul              |
| mid              | Middle                   | Ortaokul             |
| high             | Highschool               | Ortaöğretim / Lise   |
| lec              | Lecturer                 | Öğretim Üyesi        |
| p                | Private                  | Özel                 |
| s                | State                    | Devlet / Resmi       |
| 22_23            | 22-23 Schooling Year     | 22-23 Eğitim Yılı    |
| prof             | Professor                | Profesör             |
| assocprof        | Associate Prof.          | Doçent               |
| assistprof       | Assistant Prof.          | Dr. Öğretim Üyesi    |
| lecturer         | Lecturer (Dr.)           | Öğretim Görevlisi    |
| researchassist   | Research Assistant       | Araştırma Görevlisi  |
| assoc            | Associate's Degree       | Önlisans             |
| bach             | Bachelor's Degree        | Lisans               |
| master           | Master's Degree          | Yükseklisans         |
| doc              | Doctorate Degree         | Doktora              |
| daytime          | Daytime / Regular Class  | I. Öğretim           |
| evening          | Evening Class            | II. Öğretim          |
| voc              | Vocational               | Mesleki              |


Additionally, explanations for each dataset are shared with PDF files. This project is open to suggestions from contributors who want to contribute.


****
<p align="center">
[TÜRKÇE] <img src="https://github.com/jackiboy/flagpack/blob/master/flags/4x3/tr.svg" width="16" height="12">
</p>

Bu dosya özellikle harita ile veri görselleştirme yapmak için hazırlanmıştır. Dosyadaki veri setlerindeki veriler resmi kurum ve kuruluşların web sitelerinden elde edilmiştir. Veri setleri, bu veri setlerindeki bir değişken (gadm_L3number) sayesinde gadm.org’dan ücretsiz olarak indirilebilecek level-1 Türkiye (iller) verisi birleştirilebilir, ardından veri görselleştirmesi yapılabilir. Bunun için bir örnek R satır komutu ve bu komut ile elde edilen çıktı aşağıda verilmiştir.

```
library(sf)
library(dplyr)
library(ggplot2)

TR1 <- read_sf("C:/Your_Directory/gadm41_TUR_1.shp")
TR_coord <- st_coordinates(TR1)

TR_coord <- fortify(as_tibble(TR_coord))
TREduData_literacy <- read.csv("https://raw.githubusercontent.com/gungorMetehan/TREduData/main/TREduData_literacy.csv")

TR_Data <- TR_coord %>%
  full_join(x =., y = TREduData_literacy, by = c("L3" = "gadm_L3number"))

TR_Data %>% ggplot(aes(x = X, y = Y, group = L3, fill = literacyrate_2022)) +
  geom_polygon() +
  coord_fixed() +
  theme_void() +
  scale_fill_viridis_c(option = "D") +
  guides(fill = guide_legend("2022 - Okuryazarlık Oranı")) +
  theme(legend.position = "bottom")
```
![Rplot02](https://github.com/gungorMetehan/TREduData/assets/102655648/6f8dd21a-399c-4fe4-addf-763d2b4e7729)

Bu dosya aşağıdaki veri setlerini içermektedir:
1) TREduData_class: İllerdeki ilköğretim ve ortaöğretim okullarındaki dersliklere ilişkin verileri içermektedir.
2) TREduData_exam: Türkiye’deki çeşitli sınavlar ile ilgili verileri içermektedir.
3) TREduData_literacy: İllere göre okuryazarlık ile ilgili verileri içermektedir.
4) TREduData_school: İllerdeki ilköğretim ve ortaöğretim okullarına ilişkin verileri içermektedir.
5) TREduData_student: İllerdeki ilköğretim ve ortaöğretim okullarındaki öğrencilere ilişkin verileri içermektedir.
6) TREduData_teacher: İllerdeki ilköğretim ve ortaöğretim okullarındaki öğretmenlere ilişkin verileri içermektedir.
7) TREduData_university: İllerdeki üniversitelere ilişkin verileri içermektedir.

Değişken İsimlerindeki Kısaltmalar
| Kod              | İngilizce                | Türkçe               |
| ---------------- | ------------------------ | -------------------- |
| m                | Male                     | Erkek                |
| f                | Female                   | Kadın                |
| num              | Number                   | Sayı / Sayısı        |
| stu              | Student                  | Öğrenci              |
| pre              | Preschool                | Okul Öncesi          |
| ele              | Elementary               | İlkokul              |
| mid              | Middle                   | Ortaokul             |
| high             | Highschool               | Ortaöğretim / Lise   |
| lec              | Lecturer                 | Öğretim Üyesi        |
| p                | Private                  | Özel                 |
| s                | State                    | Devlet / Resmi       |
| 22_23            | 22-23 Schooling Year     | 22-23 Eğitim Yılı    |
| prof             | Professor                | Profesör             |
| assocprof        | Associate Prof.          | Doçent               |
| assistprof       | Assistant Prof.          | Dr. Öğretim Üyesi    |
| lecturer         | Lecturer (Dr.)           | Öğretim Görevlisi    |
| researchassist   | Research Assistant       | Araştırma Görevlisi  |
| assoc            | Associate's Degree       | Önlisans             |
| bach             | Bachelor's Degree        | Lisans               |
| master           | Master's Degree          | Yükseklisans         |
| doc              | Doctorate Degree         | Doktora              |
| daytime          | Daytime / Regular Class  | I. Öğretim           |
| evening          | Evening Class            | II. Öğretim          |
| voc              | Vocational               | Mesleki              |

Ayrıca her bir veri seti için açıklamalar PDF dosyaları ile paylaşılmıştır. Bu proje, katkı sunmak isteyenlerin önerilerine açıktır.
