# Применение итогового датасета 
﻿Датасет предназначен для арендодателей *для определения ценности сдачи жилья* через marketplace AirBnb (Airbnb, Inc — американская компания в сфере онлайн-бронирования жилья, в первую очередь для краткосрочной аренды в рамках туристических и деловых поездок. Базирующаяся в Сан-Франциско, Калифорния, платформа доступна через веб-сайт и мобильное приложение).

Например, с *определенными допущениями можно высчитать загрузку объекта* (число дней в году, когда объект сдается) и высчитать приведенный доход на человека или на спальное место. 
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

По итогам экспертного анализа по более 100 изначальных признаков было решение оставить следующие (название признаков в данном случае чаще всего говорит само за себя, тем не менее, к большинству даны пояснения):

 0   id                                            int64  
 1   last_scraped                                  object *последняя дата парсинга*
 2   name                                          object *имя листинга*
 3   summary                                       object *саммари объекта аренды*
 4   space                                         object *описание географического расположения объекта*
 5   description                                   object *описание самого объекта*
 6   experiences_offered                           object *онлайн активности хоста*
 7   neighborhood_overview                         object *описание территориальной единицы*
 8   notes                                         object *заметки хоста*
 9   transit                                       object *транспортная доступность*
 10  access                                        object *подробности по включенным опциям*
 11  interaction                                   object 
 12  house_rules                                   object *правила проживания*
 13  picture_url                                   object *ссылка на картинку объекта*
 14  host_id                                       int64  *id хоста*
 15  host_url                                      object *фото хоста*
 16  host_name                                     object *имя хоста*
 17  host_location                                 object *мы можем использовать его, чтобы установить, является ли хост местным или нет*
 18  host_about                                    object *о хосте*
 19  host_response_time                            object 
 20  host_response_rate                            object 
 21  host_acceptance_rate                          object 
 22  host_is_superhost                             object *является ли хост превосходным, зависит от общего отзыва*
 23  host_picture_url                              object 
 24  host_neighbourhood                            object 
 25  host_listings_count                           float64
 26  host_total_listings_count                     float64
 27  host_verifications                            object 
 28  host_has_profile_pic                          object *есть ли у хоста фото*
 29  host_identity_verified                        object *проверен ли хост*
 30  street                                        object 
 31  neighbourhood                                 object 
 32  neighbourhood_cleansed                        object *уровень административно-территориальной принадлежности*
 33  neighbourhood_group_cleansed                  object *более высокий, чем neighbourhood_cleansed уровень административно-территориальной принадлежности* 
 34  state                                         object 
 35  zipcode                                       object 
 36  market                                        object 
 37  smart_location                                object 
 38  latitude                                      float64
 39  longitude                                     float64
 40  is_location_exact                             object 
 41  property_type                                 object 
 42  room_type                                     object 
 43  accommodates                                  int64  *количество мест*
 44  bathrooms                                     float64 *количество ванн*
 45  bedrooms                                      float64 *количество спален*
 46  beds                                          float64 *количество кроватей*
 47  bed_type                                      object *тип кровати*
 48  amenities                                     object *удобства*
 49  square_feet                                   float64
 50  price                                         float64
 51  weekly_price                                  object 
 52  monthly_price                                 object 
 53  security_deposit                              object 
 54  cleaning_fee                                  object 
 55  guests_included                               int64  
 56  extra_people                                  object 
 57  minimum_nights                                int64  
 58  maximum_nights                                int64  
 59  calendar_updated                              object 
 60  availability_30                               int64  
 61  availability_90                               int64  
 62  availability_365                              int64  
 63  number_of_reviews                             int64  
 64  first_review                                  object 
 65  last_review                                   object 
 66  review_scores_rating                          float64
 67  review_scores_accuracy                        float64
 68  review_scores_cleanliness                     float64
 69  review_scores_checkin                         float64
 70  review_scores_communication                   float64
 71  review_scores_location                        float64
 72  review_scores_value                           float64
 73  requires_license                              object 
 74  license                                       object 
 75  jurisdiction_names                            object 
 76  instant_bookable                              object 
 77  is_business_travel_ready                      object 
 78  cancellation_policy                           object 
 79  require_guest_profile_picture                 object 
 80  require_guest_phone_verification              object 
 81  reviews_per_month                             float64
 82  df_city                                       object 
 83  maximum_maximum_nights                        float64
 84  number_of_reviews_ltm                         float64
 85  calculated_host_listings_count_entire_homes   float64
 86  calculated_host_listings_count_private_rooms  float64
 87  calculated_host_listings_count_shared_rooms   float64

Исходя из содержания столбцов, мы пришли к выводу, что можем удалить столбцы listing_url, thumbnail_url, medium_url, xl_picture_url, country_code, country, has_availability.
В дополнение к этому, были были удалены сильно скоррелированные признаки:
'maximum_nights_avg_ntm', 'minimum_nights_avg_ntm', 'minimum_maximum_nights', 'minimum_maximum_nights', 'city', 'calculated_host_listings_count', 'minimum_minimum_nights', 'minimum_nights_avg_ntm', 'minimum_minimum_nights', 'jurisdiction_names', 'maximum_minimum_nights', 'medium_url', 'thumbnail_url', 'df_city', 'maximum_minimum_nights', 'availability_60'.
  
После анализа было решено оставить столбцы, которые могут быть полезны при дальнейшем глубоком анализе, например, может пригодиться name хоста в случае парсинга пользователями набора данных столбцов summary или house_rules, а picture_url может пригодитьсядля понимания, есть ли вообще картинка у предложения.


## Список источников
[https://www.kaggle.com/datasets/broach/denverairbnb?select=listings.csv](https://www.kaggle.com/datasets/broach/denverairbnb?select=listings.csv "https://www.kaggle.com/datasets/broach/denverairbnb?select=listings.csv")
[https://www.kaggle.com/datasets/airbnb/seattle](https://www.kaggle.com/datasets/airbnb/seattle "https://www.kaggle.com/datasets/airbnb/seattle")
[https://www.kaggle.com/datasets/airbnb/boston](https://www.kaggle.com/datasets/airbnb/boston "https://www.kaggle.com/datasets/airbnb/boston")
[https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata](https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata "https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata")
