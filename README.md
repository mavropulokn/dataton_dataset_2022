
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

По итогам экспертного анализа по более 100 изначальных признаков было решение оставить следующие (название признаков в данном случае чаще всего говорит само за себя, тем не менее, к некоторым даны пояснения):


 - 0   id                                            int64  

 - 1   last_scraped                                  object 

 - 2   name                                          object 

 - 3   summary                                       object 

 - 4   space                                         object 

 - 5   description                                   object 

 - 6   experiences_offered                           object 

 - 7   neighborhood_overview                         object 

 - 8   notes                                         object 

 - 9   transit                                       object 

 - 10  access                                        object 

 - 11  interaction                                   object 

 - 12  house_rules                                   object 

 - 13  picture_url                                   object 

 - 14  host_id                                       int64  

 - 15  host_url                                      object 

 - 16  host_name                                     object 

 - 17  host_location                                 object 

 - 18  host_about                                    object 

 - 19  host_response_time                            object 

 - 20  host_response_rate                            object 

 - 21  host_acceptance_rate                          object 

 - 22  host_is_superhost                             object 

 - 23  host_picture_url                              object 

 - 24  host_neighbourhood                            object 

 - 25  host_listings_count                           float64

 - 26  host_total_listings_count                     float64

 - 27  host_verifications                            object 

 - 28  host_has_profile_pic                          object 

 - 29  host_identity_verified                        object 

 - 30  street                                        object 

 - 31  neighbourhood                                 object 

 - 32  neighbourhood_cleansed                        object 

 - 33  neighbourhood_group_cleansed                  object 

 - 34  state                                         object 

 - 35  zipcode                                       object 

 - 36  market                                        object 

 - 37  smart_location                                object 

 - 38  longitude                                     float64

 - 39  is_location_exact                             object 

 - 40  property_type                                 object 

 - 41  room_type                                     object 

 - 42  accommodates                                  int64  

 - 43  bathrooms                                     float64

 - 44  bedrooms                                      float64

 - 45  beds                                          float64

 - 46  bed_type                                      object 

 - 47  amenities                                     object 

 - 48  square_feet                                   float64

 - 49  price                                         float64

 - 50  weekly_price                                  object 

 - 51  monthly_price                                 object 

 - 52  security_deposit                              object 

 - 53  cleaning_fee                                  object 

 - 54  guests_included                               int64  

 - 55  extra_people                                  object 

 - 56  minimum_nights                                int64  

 - 57  maximum_nights                                int64  

 - 58  calendar_updated                              object 

 - 59  availability_30                               int64  

 - 60  availability_90                               int64  

 - 61  availability_365                              int64  

 - 62  number_of_reviews                             int64  

 - 63  first_review                                  object 

 - 64  last_review                                   object 

 - 65  review_scores_rating                          float64

 - 66  review_scores_accuracy                        float64

 - 67  review_scores_cleanliness                     float64

 - 68  review_scores_checkin                         float64

 - 69  review_scores_communication                   float64

 - 70  review_scores_location                        float64

 - 71  review_scores_value                           float64

 - 72  requires_license                              object 

 - 73  license                                       object 

 - 74  jurisdiction_names                            object 

 - 75  instant_bookable                              object 

 - 76  is_business_travel_ready                      object 

 - 77  cancellation_policy                           object 

 - 78  require_guest_profile_picture                 object 

 - 79  require_guest_phone_verification              object 

 - 80  reviews_per_month                             float64

 - 81  df_city                                       object 

 - 82  maximum_maximum_nights                        float64

 - 83  number_of_reviews_ltm                         float64

 - 84  calculated_host_listings_count_entire_homes   float64

 - 85  calculated_host_listings_count_private_rooms  float64

 - 86  calculated_host_listings_count_shared_rooms   float64

Исходя из содержания столбцов, мы пришли к выводу, что можем удалить столбцы listing_url, thumbnail_url, medium_url, xl_picture_url, country_code, country, has_availability.
В дополнение к этому, были были удалены сильно скоррелированные признаки:
'maximum_nights_avg_ntm', 'minimum_nights_avg_ntm', 'minimum_maximum_nights', 'minimum_maximum_nights', 'city', 'calculated_host_listings_count', 'minimum_minimum_nights', 'minimum_nights_avg_ntm', 'minimum_minimum_nights', 'jurisdiction_names', 'maximum_minimum_nights', 'medium_url', 'thumbnail_url', 'df_city', 'maximum_minimum_nights', 'availability_60'.
  
После анализа было решено оставить столбцы, которые могут быть полезны при дальнейшем глубоком анализе, например, может пригодиться name хоста в случае парсинга пользователями набора данных столбцов summary или house_rules, а picture_url может пригодитьсядля понимания, есть ли вообще картинка у предложения.

## Ссылки на датасеты
Входной датасет
[https://drive.google.com/file/d/1Q56Hr8nsos65R0Hcn1wJ6On84LjfLUQg/view?usp=share_link](https://drive.google.com/file/d/1Q56Hr8nsos65R0Hcn1wJ6On84LjfLUQg/view?usp=share_link "https://www.kaggle.com/datasets/broach/denverairbnb?select=listings.csv")

Датасет после минимальной обработки
[https://drive.google.com/file/d/1Qf1fsuvjinIQM3IiqgpOcSTpcw2tM33G/view?usp=share_link](https://drive.google.com/file/d/1Qf1fsuvjinIQM3IiqgpOcSTpcw2tM33G/view?usp=share_link "https://drive.google.com/file/d/1Qf1fsuvjinIQM3IiqgpOcSTpcw2tM33G/view?usp=share_link")

## Список источников
[https://www.kaggle.com/datasets/broach/denverairbnb?select=listings.csv](https://www.kaggle.com/datasets/broach/denverairbnb?select=listings.csv "https://www.kaggle.com/datasets/broach/denverairbnb?select=listings.csv")

[https://www.kaggle.com/datasets/airbnb/seattle](https://www.kaggle.com/datasets/airbnb/seattle "https://www.kaggle.com/datasets/airbnb/seattle")

[https://www.kaggle.com/datasets/airbnb/boston](https://www.kaggle.com/datasets/airbnb/boston "https://www.kaggle.com/datasets/airbnb/boston")

[https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata](https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata "https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata")
