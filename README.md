# Применение итогового датасета 
﻿Датасет предназначен для арендодателей *для определения ценности сдачи жилья* через marketplace AirBnb (Airbnb, Inc — американская компания в сфере онлайн-бронирования жилья, в первую очередь для краткосрочной аренды в рамках туристических и деловых поездок. Базирующаяся в Сан-Франциско, Калифорния, платформа доступна через веб-сайт и мобильное приложение).

Например, с *определенными допущениями можно высчитать загрузку объекта* (число дней в году, когда объект сдается) и высчитать приведенный доход на человека или на спальное место:
- **сгенерирован признак prognosed_occupancy_days_per_year** - рассчитан на с использованием открытой в 2012 году информации о том, что 72% всех гостей оставляют отзывы, то есть делится количество всех отзывов на 0.72 (получаем фактическое примерное количество заездов), далее умножается на минимальное число дней для бронирования и делится на период в днях, за который были собраны отзывы (то есть получается относительная загрузка по времени объекта аренды), умножается на 365 дней (количество дней, когда объект загружен);
- также **сгенерирован признак prognosed_income_per_year**, путем умножения prognosed_occupancy_days_per_year на цену за день (**без учета инфляции*)

**Выводы по визуальному анализу находятся в notebook файле в данном репозитории.**

Конечно же, датасет содержит расположение объектов и по столбцам можно понять о качестве объекта и наличии удобств, техники. 
Более того, признаков достаточно для глубокого анализа (например, сохранено имя объекта для тех пользователей датасета, кто захочет найти упоминание имени в саммари или прочих текстовых столбцах для анализа тональности), то есть при глубоком анализе можно сделать вывод, каким может быть эффективное описание или саммари объекта и требования квартиросъемщику.

Кроме этого, можно заиспользовать id в будущем для мерджа с другими датасетами, а также добавить базу продаж объектов по тем же адресам, что могло бы дать возможность рассчитать прогнозную числую приведенную стоимость инвестиции в недвижимость (прибыль) с учетом затрат на покупку объекта недвижимости, в добавок к тому, что уже сейчас можно рассчитать (например, прогнозную приведенную стоимость арендных платежей).


# Детальное описание датасета

В итоговый датасет вошли данные из четырех датасетов по предложениям бронирования в Нью-Йорке, Бостоне, Денвере и Сиэтле. 

## Основные параметры

В итоговом датасете содержится следующая информация:
 - Полные описания предложений аренды
 - Информация о владельце и его требования
 - Информацию о рейтингах объекта от пользователей сервиса

## Структура

По итогам экспертного анализа по более 100 изначальных признаков было решение оставить следующие (название признаков в данном случае чаще всего говорит само за себя, тем не менее, к некоторым даны пояснения):

 - 0 id int64 *id листинга*
 - 1 last_scraped object	*последняя дата парсинга*
 - 2 name object	*имя листинга*
 - 3 summary object	*саммари объекта аренды*
 - 4 space object	*описание географического расположения объекта*
 - 5 description object	*описание самого объекта*
 - 6 experiences_offered object	*онлайн активности хоста*
 - 7 neighborhood_overview object	*описание административно-территориальной единицы*
 - 8 notes object	*заметки хоста*
 - 9 transit object	*транспортная доступность*
 - 10 access object	*подробности по включенным опциям*
 - 11 interaction object
 - 12 house_rules object	*правила проживания*
 - 13 picture_url object	*ссылка на картинку объекта*
 - 14 host_id int64	*id хоста*
 - 15 host_url object
 - 16 host_name object	*имя хоста*
 - 17 host_location object	*мы можем использовать его, чтобы установить, является ли хост местным или нет*
 - 18 host_about object	*о хосте, текст*
 - 19 host_response_time object	*время ответа, в единицах времени*
 - 20 host_response_rate object
 - 21 host_acceptance_rate object
 - 22 host_is_superhost object	*является ли хост превосходным, зависит от общего отзыва*
 - 23 host_picture_url object	*ссылка на объект*
 - 24 host_neighbourhood object	*административно-территориальная единица*
 - 25 host_listings_count float64	
 - 26 host_total_listings_count float64	
 - 27 host_verifications object	*проверка хозяина, список*
 - 28 host_has_profile_pic object	*есть ли у хоста фото*
 - 29 host_identity_verified object	*идентифицирован ли хост*
 - 30 street object	*улица*
 - 31 neighbourhood object	*соседство*
 - 32 neighbourhood_cleansed object	*уровень административно-территориальной принадлежности*
 - 33 neighbourhood_group_cleansed object	*более высокий, чем neighbourhood_cleansed уровень административно-территориальной принадлежности*
 - 34 state object	*штат*
 - 35 zipcode object	*почтовый индекс*
 - 36 market object
 - 37 smart_location object	*расположение*
 - 38 longitude float64	*долгота*
 - 39 is_location_exact object	*расположение точное или нет*
 - 40 property_type object	*тип недвижимости*
 - 41 room_type object	*тип комнат*
 - 42 accommodates int64	*вместимость, кол-во арендаторов*
 - 43 bathrooms float64	*количество ванных*
 - 44 bedrooms float64	*количество спален*
 - 45 beds float64	*количество кроватей*
 - 46 bed_type object	*тип кровати*
 - 47 amenities object	*включенный список услуг*
 - 48 square_feet float64	*площадь*
 - 49 price float64	*цена за день*
 - 50 weekly_price object	*цена за неделю*
 - 51 monthly_price object	*цена за месяц*
 - 52 security_deposit object	*предоплата*
 - 53 cleaning_fee object	*комиссия за уборку*
 - 54 guests_included int64	*количество гостей*
 - 55 extra_people object	*дополнительные места*
 - 56 minimum_nights int64	*минимальное количество ночей*
 - 57 maximum_nights int64	*максимальное количество ночей*
 - 58 calendar_updated object
 - 59 availability_30 int64	*доступность снятия 30*
 - 60 availability_90 int64	*доступность сняти 90*
 - 61 availability_365 int64	*доступность снятия 365*
 - 62 number_of_reviews int64	*количество отзывов*
 - 63 first_review object	*дата, первый обзор*
 - 64 last_review object	*дата, последний обзор*
 - 65 review_scores_rating float64	*общая оценка*
 - 66 review_scores_accuracy float64	*оценка соответствия*
 - 67 review_scores_cleanliness float64	*совокупная оценка по парамтру airbnb*
 - 68 review_scores_checkin float64	*оценка заселения*
 - 69 review_scores_communication float64	*оценка коммуникации с хостом*
 - 70 review_scores_location float64	*оценка локации*
 - 71 review_scores_value float64	*оценка цены*
 - 72 requires_license object
 - 73 license object
 - 74 jurisdiction_names object	*юрисдикция/штат*
 - 75 instant_bookable object	*возможность мгновенного бронирования*
 - 76 is_business_travel_ready object
 - 77 cancellation_policy object	*политика отмены бронирования*
 - 78 require_guest_profile_picture object	*требуется фотография профиля гостя*
 - 79 require_guest_phone_verification object	*требуется подтверждение номера телефона гостя*
 - 80 reviews_per_month float64	*количество отзывов в месяц*
 - 81 df_city object *город*
 - 82 maximum_maximum_nights float64	
 - 83 number_of_reviews_ltm float64	
 - 84 calculated_host_listings_count_entire_homes float64	
 - 85 calculated_host_listings_count_private_rooms float64	
 - 86 calculated_host_listings_count_shared_rooms float64
 - 87  prognosed_occupancy_days_per_year             float64 *прогнозная загрузка объекта аренды, дней в году*      
 - 88  prognosed_income_per_year                     float64 *прогнозный доход объекта аренды, за год, на основе прогнозной загрузки, формула дана выше*      

Исходя из содержания столбцов, мы пришли к выводу, что можем удалить столбцы listing_url, thumbnail_url, medium_url, xl_picture_url, country_code, country, has_availability.
В дополнение к этому, были были удалены сильно скоррелированные признаки:
'maximum_nights_avg_ntm', 'minimum_nights_avg_ntm', 'minimum_maximum_nights', 'minimum_maximum_nights', 'city', 'calculated_host_listings_count', 'minimum_minimum_nights', 'minimum_nights_avg_ntm', 'minimum_minimum_nights', 'jurisdiction_names', 'maximum_minimum_nights', 'medium_url', 'thumbnail_url', 'df_city', 'maximum_minimum_nights', 'availability_60'.
  
После анализа было решено оставить столбцы, которые могут быть полезны при дальнейшем глубоком анализе, например, может пригодиться name хоста в случае парсинга пользователями набора данных столбцов summary или house_rules, а picture_url может пригодитьсядля понимания, есть ли вообще картинка у предложения.

## Ссылки на датасеты
[Датасет после склейки нескольких датасетов из источников](https://drive.google.com/file/d/1wrZYskv9ip9_phHSFQaCCKMeTytY7V2M/view?usp=share_link)

[Датасет после необходимой очистки от неинформативных фичей](https://drive.google.com/file/d/1_SK2dK48WFqYn0P1u1dsljkl9MBrM6wR/view?usp=share_link)

[Датасет после необходимой очистки от неинформативных фичей и трансформации признаков](https://drive.google.com/file/d/1rtQ5M5pAas0rWm0E4MIYWroArb_G44E0/view?usp=share_link)


## Список источников
[https://www.kaggle.com/datasets/broach/denverairbnb](https://www.kaggle.com/datasets/broach/denverairbnb)

[https://www.kaggle.com/datasets/airbnb/seattle](https://www.kaggle.com/datasets/airbnb/seattle)

[https://www.kaggle.com/datasets/airbnb/boston](https://www.kaggle.com/datasets/airbnb/boston)

[https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata](https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata)
