# Оценка цены предложений на жилье на AirBnb по комментариям к ним

**Airbnb, Inc** — американская компания в сфере онлайн-бронирования жилья, в первую очередь для краткосрочной аренды в рамках туристических и деловых поездок. Базирующаяся в Сан-Франциско, Калифорния, платформа доступна через веб-сайт и мобильное приложение.


# Описание датасета

В итоговый датасет вошли данные из четырех датасетов по предложениям бронирования в Нью-Йорке, Бостоне, Денвере и Сиэтле. 

## Основные параметры

В итоговом датасете содержится следующая информация:
 - Полные описания предложений и средняя оценка по отзывам
 - Обзоры, включая уникальный идентификатор для каждого рецензента и подробные комментарии
 - Календарь, включая идентификатор объявления, а также цену и доступность на этот день    
 - Районы с простыми метками

## Итоговая структура

По итогам экспертного анализа по более 100 изначальных признаков было решение оставить следующие:
**1 scrape_id** *идентификатор листинга, который можно использовать для создания соединения с другими файлами*
**2 last_scraped** *будем использовать для подсчета review_per_month* 
**3 name** *может пригодиться в дальнейшем* 
**4 summary** *может пригодиться в дальнейшем* 
**5 space** *площадь*
**6 description** *описание*
7 experiences_offered object  
8 neighborhood_overview object  
9 notes object  
10 transit object  
11 access object  
12 interaction object  
13 house_rules object  
14 picture_url object  
15 host_id int64  
16 host_url object  
**17 host_name** *может использоваться для идентификации слов, связанных с хостом в отзывах*
**18 host_since** *может использоваться для расчета опыта хоста на основе продолжительности с момента первого листинга*
**19 host_location** *мы можем использовать его, чтобы установить, является ли хост локальным или нет*
**20 host_about** *поскольку это всего лишь текст, мы будем считать количество символов*
21 host_response_time object  
22 host_response_rate object  
23 host_acceptance_rate object  
**24 host_is_superhost** *категориальное t или f — описание высоко оцененных и надежных хостов*
25 host_picture_url object  
26 host_neighbourhood object  
27 host_listings_count float64  
28 host_total_listings_count float64  
29 host_verifications object  
**30 host_has_profile_pic** *категориальный t или f — профили с картинками считаются более достоверными*
**31 host_identity_verified** *категориальный t или f — еще одна метрика достоверности*
32 street object  
33 neighbourhood object  
**34 neighbourhood_cleansed** *мы будем использовать только для визуализации из-за количества окрестностей, вместо этого мы используем сгруппированные окрестности*
**35 neighbourhood_group_cleansed** *категориальное значение, которое будет использоваться для определения наиболее популярных частей*
36 state object  
37 zipcode object  
38 market object  
39 smart_location object  
**40 latitude** *широта*
**41 longitude** *долгота*
42 is_location_exact object  
**43 property_type** *категориальная переменная*
**44 room_type** *категориальная переменная*
**45 accommodates** *дискретное значение, описывающее свойство недвижимости*
**46 bathrooms** *дискретное значение, описывающее свойство недвижимости*
**47 bedrooms** *дискретное значение, описывающее свойство недвижимости*
**48 beds** *дискретное значение, описывающее свойство недвижимости*
**49 bed_type** *дискретное значение, описывающее свойство недвижимости*
**50 amenities** *из-за количества уникальных призенаков (более 100) мы сосредоточимся только на общем количестве удобств*
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

Исходя из содержания столбцов, мы пришли к выводу, что можем **удалить** столбцы **listing_url, thumbnail_url, medium_url, xl_picture_url, country_code, country, has_availability**.
  
После анализа было решено оставить столбцы, которые могут быть полезны при дальнейшем глубоком анализе, например, может пригодиться name хоста в случае парсинга пользователями набора данных столбцов summary или house_rules, а picture_url может пригодитьсядля понимания, есть ли вообще картинка у предложения.

**Сильно скоррелированные признаки:** [('maximum_maximum_nights', 'maximum_nights_avg_ntm'), ('maximum_nights_avg_ntm', 'maximum_maximum_nights'), ('minimum_nights', 'minimum_nights_avg_ntm'), ('minimum_nights_avg_ntm', 'minimum_nights'), ('maximum_nights_avg_ntm', 'minimum_maximum_nights'), ('minimum_maximum_nights', 'maximum_nights_avg_ntm'), ('maximum_maximum_nights', 'minimum_maximum_nights'), ('minimum_maximum_nights', 'maximum_maximum_nights'), ('smart_location', 'city'), ('city', 'smart_location'), ('calculated_host_listings_count_entire_homes', 'calculated_host_listings_count'), ('calculated_host_listings_count', 'calculated_host_listings_count_entire_homes'), ('minimum_nights_avg_ntm', 'minimum_minimum_nights'), ('minimum_minimum_nights', 'minimum_nights_avg_ntm'), ('maximum_minimum_nights', 'minimum_nights_avg_ntm'), ('minimum_nights_avg_ntm', 'maximum_minimum_nights'), ('minimum_nights', 'minimum_minimum_nights'), ('minimum_minimum_nights', 'minimum_nights'), ('longitude', 'jurisdiction_names'), ('jurisdiction_names', 'longitude'), ('minimum_nights', 'maximum_minimum_nights'), ('maximum_minimum_nights', 'minimum_nights'), ('xl_picture_url', 'medium_url'), ('medium_url', 'xl_picture_url'), ('medium_url', 'thumbnail_url'), ('thumbnail_url', 'medium_url'), ('market', 'df_city'), ('df_city', 'market'), ('minimum_minimum_nights', 'maximum_minimum_nights'), ('maximum_minimum_nights', 'minimum_minimum_nights'), ('availability_90', 'availability_60'), ('availability_60', 'availability_90')]  
Признаки на удаление, кросс-корреляция выше 0.95 :  
['maximum_nights_avg_ntm', 'minimum_nights_avg_ntm', 'minimum_maximum_nights', 'minimum_maximum_nights', 'city', 'calculated_host_listings_count', 'minimum_minimum_nights', 'minimum_nights_avg_ntm', 'minimum_minimum_nights', 'jurisdiction_names', 'maximum_minimum_nights', 'medium_url', 'thumbnail_url', 'df_city', 'maximum_minimum_nights', 'availability_60'.

Таким образом, удалены за два захода столбцы по причине **повторяемости/одинаковости и по причине высокой кросс-корреляции.**
# Применение итогового датасета 
Датасет может быть использован арендодателями для определения **ценности сдачи в аренду своего жилья**. Например, с определенными допущениями можно высчитать загрузку объекта (число дней в году, когда объект сдается) и высчитать приведенный доход на человека или на спальное место. Конечно же, датасет содержит расположение объектов и по столбцам можно понять о качестве объекта и наличии удобств, техники. Более того, признаков достаточно для глубокого анализа (например, сохранено имя хоста для тех пользователей датасета, кто захочет определить упоминание имени хоста в саммари или прочих текстовых столбцах или узнать, есть ли изображение объекта), то есть **при глубоком анализе можно сделать вывод, каким может быть эффективное описание или саммари объекта и требования квартиросъемщику.**

Кроме этого, можно заиспользовать id в будущем для мерджа с другими датасетами, а также добавить базу продаж объектов по тем же адресам, что могло бы дать возможность рассчитать прогнозную числую приведенную стоимость инвестиции в недвижимость (прибыль) с учетом затрат на покупку объекта недвижимости, в добавок к тому, что уже сейчас можно рассчитать (прогнозную приведенную стоимость арендных платежей).
--- ------ -----  


## Список источников

[https://www.kaggle.com/datasets/broach/denverairbnb?select=listings.csv](https://www.kaggle.com/datasets/broach/denverairbnb?select=listings.csv "https://www.kaggle.com/datasets/broach/denverairbnb?select=listings.csv")

[https://www.kaggle.com/datasets/airbnb/seattle](https://www.kaggle.com/datasets/airbnb/seattle "https://www.kaggle.com/datasets/airbnb/seattle")

[https://www.kaggle.com/datasets/airbnb/boston](https://www.kaggle.com/datasets/airbnb/boston "https://www.kaggle.com/datasets/airbnb/boston")

[https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata](https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata "https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata")

