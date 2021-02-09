# Fantlab-API

Публичный репозиторий по API библиографического краудсорсингового портала **fantlab.ru**.   
Предназначен для:
* документирования текущего состояния API
* взаимодействия программистов FL и пользователей API через систему *Issues*/*Pull Requests*

## Вводная информация
1. API работает в тестовом режиме, текущая версия: **v0.9.\*** (*[см.историю изменений](History.md)*). До версии **1.0** возможны большие изменения в выдачах.
2. Домен для запросов - **https://api.fantlab.ru**.
3. Возможные HTTP-коды ответов: *200* (успех), *404* (ошибка запроса).
4. Из-за особенностей серверного языка (бэкенд написан на *Perl*) в выдачах уделено мало внимания типизации данных, например, вместо числа может прийти строка (e.g. `"work_id":"1"`). Это не баг. В подобных случаях в документации указан не действительный тип поля (строка), а тот, к которому можно автоматически привести (e.g. `work_id: Int`).
5. В текстовых данных могут встретиться LINK-тэги - отсылки на сущности базы - для удобства для этого используются формат html-тэга *a href*). Пример: `“notes”:”Переиздание сборника рассказов <a href=\”/work320\”>Стивен Кинг «Бегущий человек»</a>”`. Полный список сущностей базы: *autor*, *art*, *dictor*, *translator*, *person*, *work*, *edition*, *series*, *publisher*, *film*, *award*, *contest*, *user*, *topic*, *article*, *blog*, *blogarticle*. Также могут встретиться и bb-тэги вида *[user]* и т.п.. По возможности от них избавляемся, но они могут до сих пор проскакивать.
6. В случае, если тип поля в документации обозначен как *null*, это означает одно из двух: либо поле может вообще отсутствовать, либо поле есть, но его значение равно *null*. Впрочем, с точки зрения конечного пользователя это одно и то же.
7. Для удобства описания были введены дополнительные типы данных: *Boolean* ("0" (false) / "1" (true)), *Date* (строка в формате `yyyy-MM-dd`), *DateTime* (строка в формате `yyyy-MM-dd HH:mm:ss`), *Url* (ссылка на файл/картинку, обычно без протокола).
8. Если какое-нибудь поле может присутствовать или быть неравным *null* только при определенном переданном параметре, то в описании типа в этом случае указан соответствующий параметр (например, `# [biblio_blocks] список произведений`). Если поле не равно *null* при любом переданном параметре, в описании типа указан параметр `[any]`.

## Содержание
1. [Константы](Docs/config.md#Константы)
2. Поиск
    * [Миникарточки элементов базы](Docs/search-ids.md)
      * [Получение миникарточек по поисковому запросу](Docs/search-ids.md#Получение-миникарточек-по-поисковому-запросу)
      * [Получение миникарточек по их ID](Docs/search-ids.md#Получение-миникарточек-по-их-id)
    * [Поиск по библиографической базе](Docs/search.md#Поиск-по-библиографической-базе)
      * [Общий поиск](Docs/search.md#Общий-поиск)
      * [Поиск авторов](Docs/search.md#Поиск-авторов)
      * [Поиск произведений](Docs/search.md#Поиск-произведений)
      * [Поиск изданий](Docs/search.md#Поиск-изданий)
      * [Поиск книжных серий](Docs/search.md#Поиск-книжных-серий)
      * [Поиск премий](Docs/search.md#Поиск-премий)
      * [Поиск персон](Docs/search.md#Поиск-персон)
      * [Поиск издательств](Docs/search.md#Поиск-издательств)
      * [Поиск фильмов](Docs/search.md#Поиск-фильмов)
      * [Поиск статей](Docs/search.md#Поиск-статей)
    * [Поиск по форуму](Docs/search-forum.md#Поиск-по-форуму)
    * [Поиск по блогам](Docs/search-blogs.md#Поиск-по-блогам)
3. [Автор](Docs/author.md#Автор)
    * [Список авторов](Docs/author.md#Список-авторов)
    * [Основная информация](Docs/author.md#Основная-информация)
    * [Список изданий](Docs/author.md#Список-изданий)
    * [Список наград](Docs/author.md#Список-наград-отдельно)
    * [Список отзывов](Docs/responses.md#Отзывы-на-одно-произведение)
4. [Произведение](Docs/work.md#Произведение)
    * [Основная информация](Docs/work.md#Основная-информация)
    * [Расширенная информация](Docs/work.md#Расширенная-информация)
    * [Список отзывов](Docs/responses.md#Отзывы-на-одно-произведение)
    * [Похожие произведения (Аналоги)](Docs/responses.md#Похожие-произведения)
    * [Выставление/удаление оценки](Docs/work.md#Выставлениеудаление-оценки)
    * [Классификация](Docs/work.md#Классификация)
    * [Добавление похожего произведения](Docs/work.md#Добавление-похожего-произведения)
    * [Удаление похожего произведения](Docs/work.md#Удаление-похожего-произведения)
5. [Издание](Docs/edition.md#Издание)
    * [Основная информация](Docs/edition.md#Основная-информация)
    * [Расширенная информация](Docs/edition.md#Расширенная-информация)
6. [Премии](Docs/awards.md#Премии)
    * [Список премий](Docs/awards.md#Список-премий)
    * [Премия](Docs/awards.md#Премия)
    * [Конкурс](Docs/awards.md#Конкурс)
7. [Переводчик](Docs/translator.md#Переводчик)
    * [Основная информация](Docs/translator.md#Основная-информация)
    * [Список наград](Docs/translator.md#Список-наград-отдельно)
8. [Диктор](Docs/dictor.md#Диктор)
9. [Издательства](Docs/publisher.md#Издательства)
    * [Список издательств](Docs/publisher.md#Список-издательств)
    * [Топ-30 издательств](Docs/publisher.md#Топ-30-издательств)
10. [Термины](Docs//terms.md#Термины-Букопедия)
    * [Список терминов](Docs/terms.md#Список-терминов)
    * [Термин](Docs/terms.md#Термин)
10. [Пользователь](Docs/user.md#Пользователь)
    * [Основная информация](Docs/user.md#Основная-информация)
    * [Список оценок](Docs/marks.md#Оценки-посетителя)
    * [Список отзывов](Docs/responses.md#Отзывы-посетителя)
    * [Узнать id по login](Docs/user.md#Узнать-id-по-login)
11. [Отзывы](Docs/responses.md#Отзывы)
    * [Отзывы на все произведения автора](Docs/responses.md#Отзывы-на-все-произведения-автора)
    * [Отзывы на одно произведение](Docs/responses.md#Отзывы-на-одно-произведение)
    * [Отзывы посетителя](Docs/responses.md#Отзывы-посетителя)
    * [Новые отзывы на сайте](Docs/responses.md#Новые-отзывы-на-сайте)
    * [Плюсование/минусование отзыва](Docs/responses.md#Плюсованиеминусование-отзыва)
12. [Новости](Docs/news.md#Новости)
    * [Список новостей сайта](Docs/news.md#список-новостей)
13. [Новинки и планы издательств, авторов](Docs/pubnews.md)
    * [Новинки издательств](Docs/pubnews.md)
    * [Планы издательств](Docs/pubnews.md)
    * [Планы авторов](Docs/pubnews.md)
14. Авторизация
    * [OAuth](Docs/oauth.md#oauth-авторизация)
    * [Основная](Docs/auth.md#Авторизация)
15. [Подписки](Docs/subscriptions.md#Подписки)
    * [Подписка на оповещения о новых произведениях/изданиях автора](Docs/subscriptions.md#Подписка-на-оповещения-о-новых-произведениях-или-изданиях-автора)
    * [Подписка на оповещения о новых изданиях с переводами переводчика](Docs/subscriptions.md#Подписка-на-оповещения-о-новых-изданиях-с-переводами-переводчика)
    * [Отмена подписки на оповещения](Docs/subscriptions.md#Отмена-подписки-на-оповещения)
    * [Подписка на блог](Docs/subscriptions.md#Подписка-на-блог)
    * [Подписка на комментарии к статье в блоге](Docs/subscriptions.md#Подписка-на-комментарии-к-статье-в-блоге)
    * [Подписка на новые сообщения в теме форума](Docs/subscriptions.md#Подписка-на-новые-сообщения-в-теме-форума)
16. [Книжные полки](Docs/bookcases.md#Книжные-полки)
    * [Создание книжной полки](Docs/bookcases.md#Создание-книжной-полки)
    * [Удаление книжной полки](Docs/bookcases.md#Удаление-книжной-полки)
    * [Содержимое полки произведений](Docs/bookcases.md#Содержимое-полки-произведений)
    * [Содержимое полки изданий](Docs/bookcases.md#Содержимое-полки-изданий)
    * [Содержимое полки фильмов](Docs/bookcases.md#Содержимое-полки-фильмов)
    * [Добавление или удаление произведения с книжной полки](Docs/bookcases.md#Добавление-или-удаление-произведения-с-книжной-полки)
    * [Добавление или удаление издания с книжной полки](Docs/bookcases.md#Добавление-или-удаление-издания-с-книжной-полки)
    * [Добавление или удаление фильма с книжной полки](Docs/bookcases.md#Добавление-или-удаление-фильма-с-книжной-полки)
    * [Добавление комментария к item](Docs/bookcases.md#Добавление-комментария-к-item)
17. [Личка](Docs/private-messages.md#Личка)
    * [Отправка/сохранение в черновик сообщения](Docs/private-messages.md#Отправкасохранение-в-черновик-сообщения)
    * [Подтверждение отправки черновика](Docs/private-messages.md#Подтверждение-отправки-черновика)
    * [Отмена отправки черновика](Docs/private-messages.md#Отмена-отправки-черновика)
18. [Рекомендации](Docs/recommendations.md#Рекомендации)
    * [Удаление рекомендации в мусорку](Docs/recommendations.md#Удаление-рекомендации-в-мусорку)
    * [Правка мусорки рекомендаций](Docs/recommendations.md#Правка-мусорки-рекомендаций)
19. [Форум](Docs/forum.md#Форум)
    * [Плюсование/минусование поста](Docs/forum.md#Плюсованиеминусование-поста)
20. Прочее
    * [Теги, ссылки и пр.](Docs/other.md#Теги-ссылки-и-пр)
