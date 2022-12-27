# Применение итогового датасета 
Датасет предназначен для арендодателей *для определения ценности сдачи жилья* через marketplace AirBnb (Airbnb, Inc — американская компания в сфере онлайн-бронирования жилья, в первую очередь для краткосрочной аренды в рамках туристических и деловых поездок. Базирующаяся в Сан-Франциско, Калифорния, платформа доступна через веб-сайт и мобильное приложение).

Например, с *определенными допущениями можно высчитать загрузку объекта* (число дней в году, когда объект сдается) и высчитать приведенный доход на человека или на спальное место:
- **сгенерирован признак prognosed_occupancy_days_per_year** - рассчитан на с использованием открытой в 2012 году информации о том, что 72% всех гостей оставляют отзывы, то есть делится количество всех отзывов на 0.72 (получаем фактическое примерное количество заездов), далее умножается на минимальное число дней для бронирования и делится на период в днях, за который были собраны отзывы (то есть получается относительная загрузка по времени объекта аренды), умножается на 365 дней (количество дней, когда объект загружен);
- также **сгенерирован признак prognosed_income_per_year**, путем умножения prognosed_occupancy_days_per_year на цену за день (**без учета инфляции*)

**Выводы по визуальному анализу кластеризации, а также сгенерированных фичей находятся в notebook файле в данном репозитории.**

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

 - 0 id int64	
 - 1 last_scraped object	*последняя дата парсинга*
 - 2 name object	*имя листинга*
 - 3 summary object	*саммари объекта аренды*
 - 4 space object	*описание географического расположения объекта*
 - 5 description object	*описание самого объекта*
 - 6 experiences_offered object	*онлайн активности хоста*
 - 7 neighborhood_overview object	*описание территориальной единицы*
 - 8 notes object	*заметки хоста*
 - 9 transit object	*транспортная доступность*
 - 10 access object	*подробности по включенным опциям*
 - 11 interaction object	*объектов взаимодействия*
 - 12 house_rules object	*правила проживания*
 - 13 picture_url object	*ссылка на картинку объекта*
 - 14 host_id int64	*id хоста*
 - 15 host_url object	*фото хоста*
 - 16 host_name object	*имя хоста*
 - 17 host_location object	*мы можем использовать его, чтобы установить, является ли хост местным или нет*
 - 18 host_about object	*о хосте*
 - 19 host_response_time object	*время ответа*
 - 20 host_response_rate object	*скорость ответа*
 - 21 host_acceptance_rate object	*коэффициент принятия*
 - 22 host_is_superhost object	*является ли хост превосходным, зависит от общего отзыва*
 - 23 host_picture_url object	*ссылка на объект*
 - 24 host_neighbourhood object	*соседние районы*
 - 25 host_listings_count float64	
 - 26 host_total_listings_count float64	
 - 27 host_verifications object	*проверка хозяина*
 - 28 host_has_profile_pic object	*есть ли у хоста фото*
 - 29 host_identity_verified object	*проверен ли хост*
 - 30 street object	*улица*
 - 31 neighbourhood object	*соседство*
 - 32 neighbourhood_cleansed object	*уровень административно-территориальной принадлежности*
 - 33 neighbourhood_group_cleansed object	*более высокий, чем neighbourhood_cleansed уровень административно-территориальной принадлежности*
 - 34 state object	*государственный*
 - 35 zipcode object	*почтовый индекс*
 - 36 market object	*рынок*
 - 37 smart_location object	*расположение*
 - 38 latitude float64	*широта*
 - 39 longitude float64	*долгота*
 - 40 is_location_exact object	*расположение точное или нет*
 - 41 property_type object	*тип недвижимости*
 - 42 room_type object	*тип комнат*
 - 43 accommodates int64	*вместимость*
 - 44 bathrooms float64	*количество ванных*
 - 45 bedrooms float64	*количество спален*
 - 46 beds float64	*количество кроватей*
 - 47 bed_type object	*тип кровати*
 - 48 amenities object	*услуги*
 - 49 square_feet float64	*площадь*
 - 50 price float64	*цена*
 - 51 weekly_price object	*цена за неделю*
 - 52 monthly_price object	*цена за месяц*
 - 53 security_deposit object	*предоплата*
 - 54 cleaning_fee object	*комиссия*
 - 55 guests_included int64	*количество гостей*
 - 56 extra_people object	*дополнительные места*
 - 57 minimum_nights int64	*минимальное количество ночей*
 - 58 maximum_nights int64	*максимальное количество гостей*
 - 59 calendar_updated object	*календарь обновлений*
 - 60 availability_30 int64	*доступность 30*
 - 61 availability_90 int64	*доступность 90*
 - 62 availability_365 int64	*доступность 365*
 - 63 number_of_reviews int64	*количество отзывов*
 - 64 first_review object	*первый обзор*
 - 65 last_review object	*последний обзор*
 - 66 review_scores_rating float64	*баллы за отзывы*
 - 67 review_scores_accuracy float64	*оценка точности обзора*
 - 68 review_scores_cleanliness float64	*оценка частоты*
 - 69 review_scores_checkin float64	*оценка заселения*
 - 70 review_scores_communication float64	*оценка коммуникации*
 - 71 review_scores_location float64	*оценка локации*
 - 72 review_scores_value float64	*оценка итоговая*
 - 73 requires_license object	*требуемая лицензия*
 - 74 license object	*лицензия*
 - 75 jurisdiction_names object	*юрисдикция*
 - 76 instant_bookable object	*мгновенное бронирования*
 - 77 is_business_travel_ready object	*поездка деловая или нет*
 - 78 cancellation_policy object	*политика отмены бронирования*
 - 79 require_guest_profile_picture object	*требуется фотография профиля гостя*
 - 80 require_guest_phone_verification object	*требуется подтверждение номера гостевого телефона*
 - 81 reviews_per_month float64	*количество отзывов в месяц*
 - 82 df_city object	
 - 83 maximum_maximum_nights float64	
 - 84 number_of_reviews_ltm float64	*количество рецензий*
 - 85 calculated_host_listings_count_entire_homes float64	
 - 86 calculated_host_listings_count_private_rooms float64
 - 87 calculated_host_listings_count_shared_rooms float64
 - 88  prognosed_occupancy_days_per_year             float64 *прогнозная загрузка объекта аренды, дней в году*      
 - 89  prognosed_income_per_year                     float64 *прогнозный доход объекта аренды, за год, на основе прогнозной загрузки, формула дана выше*      

Исходя из содержания столбцов, мы пришли к выводу, что можем удалить столбцы listing_url, thumbnail_url, medium_url, xl_picture_url, country_code, country, has_availability.
В дополнение к этому, были были удалены сильно скоррелированные признаки: maximum_nights_avg_ntm, medium_url, maximum_minimum_nights, minimum_nights_avg_ntm,   calendar_last_scraped,   host_since,   xl_picture_url,   minimum_maximum_nights,   scrape_id,   minimum_minimum_nights, availability_60   calculated_host_listings_count.


## Ссылки на датасеты
[Датасет после склейки нескольких датасетов из источников](https://drive.google.com/file/d/1wrZYskv9ip9_phHSFQaCCKMeTytY7V2M/view?usp=share_link)

[Датасет после необходимой очистки от неинформативных фичей](https://drive.google.com/file/d/1_SK2dK48WFqYn0P1u1dsljkl9MBrM6wR/view?usp=share_link)

[Датасет после необходимой очистки от неинформативных фичей и трансформации признаков](https://drive.google.com/file/d/1rtQ5M5pAas0rWm0E4MIYWroArb_G44E0/view?usp=share_link)


## Список источников
[https://www.kaggle.com/datasets/broach/denverairbnb](https://www.kaggle.com/datasets/broach/denverairbnb)

[https://www.kaggle.com/datasets/airbnb/seattle](https://www.kaggle.com/datasets/airbnb/seattle)

[https://www.kaggle.com/datasets/airbnb/boston](https://www.kaggle.com/datasets/airbnb/boston)

[https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata](https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata)
