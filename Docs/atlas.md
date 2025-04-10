# Атлас миров

API повторяет раздел https://fantlab.ru/atlas

## Список миров
Запрос
```
GET /atlas?page={page}
```
Параметры
```
page - страница (необязательный; по-умолчанию 1). Запрос с пагинацией, отдаёт по 100 миров на странице
category - категория мира
sort - сортировка списка миров

## Информация о мире
```
GET /world/{id}
```

Пример:
> [/world/1](https://api.fantlab.ru/world/1) - Земноморье


Ответ:
```
{
    world_id: Int,               # id мира
    date_of_add: DateTime,       # время создания страницы мира
    name: String,                # название мира
    keyword: String,             # ключ сортировки
    related_work: Int,           # id связанного с миром произведения
    related_work_name: String    # название связанного с миром произведения
    titul_map_id: Int,           # id титульной карты (обложки)
    world_type_id: Int,          # id категории мира
    world_type: String,          # название категории мира
    world_maps: [
        {
            category: Int,         # тип карты (масштаб)
            map_id: Int,           # id карты
            name: String,          # название карты
            map_group: String,     # группа карты (структура отображения в мире)
            is_spoiler: Int,       # содержит ли карта спойлеры
            status_id: Int,        # статус карты (1 - официальная, 2 - издательская, 3- фанатская)_
            source: String,        # источник и/или автор карты
        },
        ...
    ],
   
