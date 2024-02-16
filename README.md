Сервис Repetit.ru работает с большим количеством заявок от клиентов с данными о предмете, желаемой стоимости, возрасте ученика, целью занятий и тд. К сожалению, 7 из 8 не доходят до оплаты, при этом обработка заявки консультантом увеличивает конверсию в оплату на 30%.
Проблема в том, что консультантов не хватает на все заявки и получается, что чем больше заявок — тем меньше конверсия из заявки в оплату и консультанты тратят время на бесперспективные заявки.


Задачей данного проекта является hазработать модель, которая по имеющейся информации о клиенте и заявке будет предсказывать вероятность оплаты заявки клиентом. Заказчик хочет понять, какие заявки будут оплачены, а какие нет, чтобы одни обрабатывать вручную консультантами, а другие нет. Оценка качества модели будет производиться с использованием precision и ROC-AUC.

Задачей является задача бинарной классификации заявок от клиентов.


В предоставленных данных есть информация о заявках с сентября/октября 2021 года по октябрь 2023 года.
В период с июля 2023 года по октябрь 2023 года произошел резкий скачек количества заявок. Заявок стало вдвое больше по сравнению со всем исследуемым периодом.

Около 200 тыс. заявок поступают вообще без указания предмета. Наиболее популярный предмет под кодом 10, а самый не популярный - 25.

Стоимость урока (lesson_price), которую пользователи указывают в заявке на поиск репетитора, составляет от 500 до 5000 рублей.

Минимальная цена (minimal_price), которую пользователи указывают в заявке на поиск репетитора, варьируется от 250 до 2000 рублей.

Минимальный возраст репетиторов в заявках варьируется от 18 до 60 лет.
Максимальный - до 100 лет.

Реальный возраст репетиторов проекта от 18 до 89 лет.

Продолжительность урока, указанная репетирами, составляет от 20 до 120 минут.
Стоимость урока, указанная репетиторами, составляет от 0 до 5000 рублей. Большинство репетиторов указывают стоимость от 500 до 1000 рублей.


Я исследовала три модели: случайного леса, LightGBM и CatBoost. Главной проблемой оказалась проблема нехватки памяти, т.к. много признаков и много строк. Я отобрала часть признаков, максимально сократила количество строк, чтобы запустить модели.
Наилучший результат показала модель CatBoost. У нее получился самый большой ROC-AUC= Наибольшее влияние на модель оказали такие признаки как: enable_auto_assign, star_rating, is_edited.