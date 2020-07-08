Утилита для импорта среднесуточных температур с сайта http://meteoinfo.ru/

Сайт гидрометцентра предоставляет информацию о фактической температуре каждые три часа. Программа считывает эти показания, усредняет и сохраняет как текущую температуру по указанной территории.

Параметры вызова программы:


--incity: Город, для которого импортируется температура. Сюда нужно передать наименование города, которое представлено на странице http://meteoinfo.ru/archive-pogoda/russia/moscow в поле выбора "Станция (город)."
Например, на сайте есть выбор "Липецк, Россия, Липецкая область". Тогда нужно передать параметр --incity "Липецк".

--utcoffset: Смещение часового пояса города относительно UTC. На сайте все даты представлены в UTC. Для пересчёта их в локальное нужно знать смещение часового пояса города относительно UTC. Например, для Липецка нужно передать --utcoffset 3, для Хабаровска --utcoffset 10

--server: Адрес сервера ЛЭРС УЧЁТ, на который нужно импортировать температуры. Необходимо указывать полный URI сервера. Например, http://localhost:10000

--login: Логин на сервере ЛЭРС УЧЁТ. Данной учётной записи должно быть разрешено редактировать среднесуточные температуры.

--password: Пароль на сервере ЛЭРС УЧЁТ.

--destTerritory: (Необязательно). Название территории на сервере ЛЭРС УЧЁТ, для которой нужно сохранить среднесуточные температуры. Если параметр не указан, температуры будут сохранены в территорию "Текущее расположение".

--importStart: (Необязательно). Дата, начиная с которой будет проводиться импорт. Если не указана, будет импортирована температура за прошлые сутки.

--importDays: (Необязательно). Если не передан параметр importStart, данные будут импортированы за последний день. Количество дней можно задать с помощью этого параметра. Например, для импорта данных за последние семь дней к параметрам вызова утилиты нужно добавить --importDays 7

--missingOnly: добавьте этот флаг для того чтобы импортировать только ту температуру, которой ещё нет в справочнике. Если параметр не задан, то все существующие в справочнике температуры за заданный интервал будут перезаписаны.

--source: сайт, с которого будут импортированы температуры. Может принимать значения:
- MeteoInfo (по умолчанию): сайт https://meteoinfo.ru
- PogodaIKlimat: сайт http://pogodaiklimat.ru/


Пример вызова:

ImportTemperatureMeteoInfo.exe --incity Хабаровск --server "server" --login "login" --password "password"
