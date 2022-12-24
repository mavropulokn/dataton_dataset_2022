# Применение итогового датасета 
﻿Датасет предназначен для арендодателей *для определения ценности сдачи жилья* через marketplace AirBnb (Airbnb, Inc — американская компания в сфере онлайн-бронирования жилья, в первую очередь для краткосрочной аренды в рамках туристических и деловых поездок. Базирующаяся в Сан-Франциско, Калифорния, платформа доступна через веб-сайт и мобильное приложение).

Например, с *определенными допущениями можно высчитать загрузку объекта* (число дней в году, когда объект сдается) и высчитать приведенный доход на человека или на спальное место. 
Конечно же, датасет содержит расположение объектов и по столбцам можно понять о качестве объекта и наличии удобств, техники. 
Более того, признаков достаточно для глубокого анализа (например, сохранено имя хоста для тех пользователей датасета, кто захочет определить упоминание имени хоста в саммари или прочих текстовых столбцах или узнать, есть ли изображение объекта), то есть при глубоком анализе можно сделать вывод, каким может быть эффективное описание или саммари объекта и требования квартиросъемщику.

Кроме этого, можно заиспользовать id в будущем для мерджа с другими датасетами, а также добавить базу продаж объектов по тем же адресам, что могло бы дать возможность рассчитать прогнозную числую приведенную стоимость инвестиции в недвижимость (прибыль) с учетом затрат на покупку объекта недвижимости, в добавок к тому, что уже сейчас можно рассчитать (например, прогнозную приведенную стоимость арендных платежей).


# Детальное описание датасета

В итоговый датасет вошли данные из четырех датасетов по предложениям бронирования в Нью-Йорке, Бостоне, Денвере и Сиэтле. 

## Основные параметры

В итоговом датасете содержится следующая информация:
 - Полные описания предложений аренды
 - Информация о владельце и его требования
 - Информацию о рейтингах объекта от пользователей сервиса

## Структура

По итогам экспертного анализа по более 100 изначальных признаков было решение оставить следующие (название признаков обычно говорит само за себя, тем не менее, к большинству даны пояснения):
1 scrape_id *идентификатор листинга, который можно использовать для создания соединения с другими файлами*
2 last_scraped *последняя дата парсинга* 
3 name *имя хоста* 
4 summary *саммари объекта* 
5 space *описание географического расположения объекта*
6 description *описание самого объекта*
7 experiences_offered - *активности хоста*
8 neighborhood_overview object *описание территориальной единицы*
9 notes object *заметки хоста*
10 transit object  *транспортная доступность*
11 access object  *подробности по включенным опциям*
12 interaction object  
13 house_rules object  *правила проживания*
14 picture_url object  *ссылка на картинку объекта*
15 host_id int64  *id хоста*
16 host_url object  *фото хоста*
17 host_name *имя хоста*
18 host_since *может использоваться для расчета опыта хоста на основе продолжительности с момента первого листинга*
19 host_location *мы можем использовать его, чтобы установить, является ли хост местным или нет*
20 host_about *о хосте*
21 host_response_time object  
22 host_response_rate object  
23 host_acceptance_rate object  
24 host_is_superhost *является ли хост превосходным, зависит от общего отзыва*
25 host_picture_url object  
26 host_neighbourhood object  
27 host_listings_count float64  
28 host_total_listings_count float64  
29 host_verifications object  
30 host_has_profile_pic *есть ли у хоста фото*
31 host_identity_verified *проверен ли хост*
32 street object  
33 neighbourhood object *низший ровень административно-территориальной принадлежности* 
34 neighbourhood_cleansed *более низкий уровень административно-территориальной принадлежности, чем neighbourhood_group_cleansed*
35 neighbourhood_group_cleansed *категориальное значение, которое будет использоваться для определения наиболее популярных частей*
36 state object  
37 zipcode object  
38 market object  
39 smart_location object  
40 latitude *широта*
41 longitude *долгота*
42 is_location_exact object  
43 property_type
44 room_type
45 accommodates *количество мест*
46 bathrooms *количество ванн*
47 bedrooms *количество спален*
48 beds *количество кроватей*
49 bed_type *тип кровати*
50 amenities *количество удобств*
51 square_feet float64  
52 price float64  
53 weekly_price object  
54 monthly_price object  
55 security_deposit object  
56 cleaning_fee object  
57 guests_included int64  
58 extra_people object  
59 minimum_nights int64  
60 maximum_nights int64  
61 calendar_updated object  
62 availability_30 int64  
63 availability_90 int64  
64 availability_365 int64
65 calendar_last_scraped object  
66 number_of_reviews int64  
67 first_review object  
68 last_review object  
69 review_scores_rating float64  
70 review_scores_accuracy float64  
71 review_scores_cleanliness float64  
72 review_scores_checkin float64  
73 review_scores_communication float64  
74 review_scores_location float64  
75 review_scores_value float64  
76 requires_license object  
77 license object  
78 instant_bookable object  
79 is_business_travel_ready object  
80 cancellation_policy object  
81 require_guest_profile_picture object  
82 require_guest_phone_verification object  
83 reviews_per_month float64  
84 maximum_maximum_nights float64  
85 number_of_reviews_ltm float64  
86 calculated_host_listings_count_entire_homes float64  
87 calculated_host_listings_count_private_rooms float64  
88 calculated_host_listings_count_shared_rooms float64

Исходя из содержания столбцов, мы пришли к выводу, что можем удалить столбцы listing_url, thumbnail_url, medium_url, xl_picture_url, country_code, country, has_availability.
В дополнение к этому, были были удалены сильно скоррелированные признаки:
'maximum_nights_avg_ntm', 'minimum_nights_avg_ntm', 'minimum_maximum_nights', 'minimum_maximum_nights', 'city', 'calculated_host_listings_count', 'minimum_minimum_nights', 'minimum_nights_avg_ntm', 'minimum_minimum_nights', 'jurisdiction_names', 'maximum_minimum_nights', 'medium_url', 'thumbnail_url', 'df_city', 'maximum_minimum_nights', 'availability_60'.
  
После анализа было решено оставить столбцы, которые могут быть полезны при дальнейшем глубоком анализе, например, может пригодиться name хоста в случае парсинга пользователями набора данных столбцов summary или house_rules, а picture_url может пригодитьсядля понимания, есть ли вообще картинка у предложения.



## Список источников
[https://www.kaggle.com/datasets/broach/denverairbnb?select=listings.csv](https://www.kaggle.com/datasets/broach/denverairbnb?select=listings.csv "https://www.kaggle.com/datasets/broach/denverairbnb?select=listings.csv")
[https://www.kaggle.com/datasets/airbnb/seattle](https://www.kaggle.com/datasets/airbnb/seattle "https://www.kaggle.com/datasets/airbnb/seattle")
[https://www.kaggle.com/datasets/airbnb/boston](https://www.kaggle.com/datasets/airbnb/boston "https://www.kaggle.com/datasets/airbnb/boston")
[https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata](https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata "https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata")
