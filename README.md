# hh_hw_architecture
## Ответы:  
### 1) Представим, что у нас есть данные, которые мы очень часто читаем по сравнению с другими(например словарь стран). Как можно это оптимизировать?  
-        Можно добавить кэширование для самых популярных запросов.  
-        Можно вывести (берем пример - словарь стран) в отдельную бд, что бы разгрузить основную.
### 2) Что можно сделать, если таблица вакансий стала слишком большой? Какие есть решения на уровне текущей базы данных? Можно ли ее чем то заменить?
-        Проиндексировать таблицу/пересмотреть индексы.
-        Можно разбить таблицу на несколько меньших по какому-либо совпадающему полю, например по регионам, необходимому опыту работы и т.п.
-        Можно выгрузить старые/не популярные вакансии в отдельную бд.
### 3) Какие вы видите узкие места, возможно неправильно выбранные технологии в текущей схеме(можно рассмотреть как “нашу” схему, так и схему настоящего hh.ru)
#### Здесь я возьму схему с нашей лекции, т.к. опыта не хватает что-то комментировать по схеме настоящего хх, так что не судите строго, пожалуйста).
По схеме с лекции:
-        сделал бы больше реплик, сделал бы чтение из реплик воркером через балансировщик
-        добавил бы кэш для хранения результатов самых популярных запросов.
-        добавил бы облачное хранилище для логотипов компаний, фотографий пользователей, хранения видео-презентаций компании и прочих файлов.
-        возможно, имеет смысл добавить отдельный сервис, который будет работать автоматически с отдельной репликой бд и периодически формировать и обновлять готовые результаты на самые ресурсоемкие запросы и кидать их в кэш.
