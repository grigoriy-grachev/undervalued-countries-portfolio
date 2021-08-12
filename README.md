# Сбор информации и составление долей портфеля из акций недооцененных стран

## Цель работы скрипта
Составить портфель из индексных фондов недооцененных стран

## Алгоритм
Для каждой страны собираются данные по двум коэффициентам:

-	Shiller PE (CAPE)
-	Price to Book value (P/B)


CAPE собирается с двух источников: 

-	https://indices.barclays/
-	https://www.researchaffiliates.com/

Их данные могут различаться, но корреляция всегда есть.


PB собирается с сайта https://www.etf.com. Selenium собирает примерно за 10 минут.


На основе трех коэффициентов (один PB и два CAPE) вычисляем усреднённый коэффициент aggregated_factor. Используем в портфеле топ-10 стран с самым низким aggregated_factor. Доли в портфеле обратно пропорциональны aggregated_factor.

## Общие рекомендации
Ребалансировка портфеля примерно раз в квартал.

Данная информация не является инвестиционной рекомендацией. Не следует инвестировать в то, что не понимаете.

Последний результат работы скрипта https://docs.google.com/spreadsheets/d/1r3pmRTKgIj2HthrY7f6PG63lWesYYIEeN8Q6XvOd_jI/

## Особенности запуска
Для запуска скрипта потребуется Selenium WebDriver.
Путь до вашего вебдрайвера должен быть прописан в переменной executable_path


В последней ячейке отправка данных в google таблицу (необязательный шаг). Для этого потребуется 
1. Cоздать проект в google cloud 
2. Получить от него токен доступа (указать в filename)
3. Создать файл google sheets (адрес указать в google_sheet)
4. Отправить от этого google sheet доступ на редактирование этому проекту

  Инструкция по интеграции с google  sheets https://docs.gspread.org/en/latest/oauth2.html#enable-api-access-for-a-project

