# Лабораторная работа 1.1: Обработка данных из БД с помощью Pandas и SQLite

**Студент:** Ежергин Святослав Сергеевич  
**Вариант:** 13

## Описание работы
В рамках лабораторной работы выполнены 5 заданий на обработку данных из базы данных `chinook.db` с использованием:
- SQL-запросов для извлечения данных
- Библиотеки Pandas для анализа и преобразования данных

## Содержание репозитория
- `lab1_1.ipynb` - Jupyter Notebook с выполненными заданиями
- `chinook.db` - база данных для выполнения работы
- `README.md` - описание работы (этот файл)

## Выполненные задания (Вариант 13)

### 1. Фильтрация по диапазону
Найти все треки, длительность которых находится между 3 и 4 минутами (180000 и 240000 мс).

### 2. Объединение таблиц (JOIN)
Вывести имена клиентов и их email, которые покупали треки жанра 'Classical'.

### 3. Агрегация и группировка
Посчитать, сколько раз был продан каждый трек. Вывести топ-10 самых продаваемых треков.

### 4. Обработка данных в Pandas
Получить все треки с их ценой. Создать столбец `PriceCategory`:
- 'Standard' для цены 0.99
- 'Premium' для цены 1.99
- 'Other' для остальных

### 5. Анализ временных рядов в Pandas
Получить все счета. Рассчитать нарастающий итог по сумме продаж в хронологическом порядке.

## Требования к запуску
Для запуска кода необходимо:
1. Установить Python 3.7+
2. Установить необходимые библиотеки:
   ```bash
   pip install pandas sqlite3

3. Запустить Jupyter Notebook:
    ```bash
    jupyter notebook lab1_1.ipynb

## Структура базы данных
База данных `chinook.db` содержит информацию о музыкальном магазине:

- `artists`, `albums`, `tracks` - информация об исполнителях и треках
- `genres`, `media_types` - справочники жанров и типов медиа
- `customers`, `invoices`, `invoice_items` - информация о клиентах и продажах
- `employees` - сотрудники магазина

## Результаты выполнения

### 1. Треки от 3 до 4 минут (первые 10)
| TrackId | Name                      | Milliseconds |
|---------|---------------------------|--------------|
| 3       | Fast As a Shark           | 230619       |
| 6       | Put The Finger On You     | 205662       |
| 7       | Let's Get It Up           | 233926       |
| 8       | Inject The Venom          | 210834       |
| 9       | Snowballed                | 203102       |
| 11      | C.O.D.                    | 199836       |
| 13      | Night Of The Long Knives  | 205688       |
| 16      | Dog Eat Dog               | 215196       |
| 32      | Deuces Are Wild           | 215875       |
| 40      | Perfect                   | 188133       |

### 2. Клиенты, покупавшие Classical
| FirstName  | LastName  | Email                          |
|------------|-----------|--------------------------------|
| Camille    | Bernard   | camille.bernard@yahoo.fr       |
| Marc       | Dubois    | marc.dubois@hotmail.com        |
| Luís       | Gonçalves | luisg@embraer.com.br           |
| Patrick    | Gray      | patrick.gray@aol.com           |
| Astrid     | Gruber    | astrid.gruber@apple.at         |
| Bjørn      | Hansen    | bjorn.hansen@yahoo.no          |
| Lucas      | Mancini   | lucas.mancini@yahoo.it         |
| Isabelle   | Mercier   | isabelle_mercier@apple.fr      |
| Manoj      | Pareek    | manoj.pareek@rediff.com        |
| Frank      | Ralston   | fralston@gmail.com             |
| Fernanda   | Ramos     | fernadaramos4@uol.com.br       |
| Luis       | Rojas     | luisrojas@yahoo.cl             |
| Ellie      | Sullivan  | ellie.sullivan@shaw.ca         |
| François   | Tremblay  | ftremblay@gmail.com            |

### 3. Топ-10 самых продаваемых треков
| TrackName                         | TimesSold |
|-----------------------------------|-----------|
| Balls to the Wall                 | 2         |
| Inject The Venom                  | 2         |
| Snowballed                        | 2         |
| Overdose                          | 2         |
| Deuces Are Wild                   | 2         |
| Not The Doctor                    | 2         |
| Por Causa De Você                 | 2         |
| Welcome Home (Sanitarium)         | 2         |
| Snowblind                         | 2         |
| Cornucopia                        | 2         |

### 4. Треки с категорией цены (первые 10)
| TrackId | Name                                    | UnitPrice | PriceCategory |
|---------|-----------------------------------------|-----------|---------------|
| 1       | For Those About To Rock (We Salute You) | 0.99      | Standard      |
| 2       | Balls to the Wall                       | 0.99      | Standard      |
| 3       | Fast As a Shark                         | 0.99      | Standard      |
| 4       | Restless and Wild                       | 0.99      | Standard      |
| 5       | Princess of the Dawn                    | 0.99      | Standard      |
| 6       | Put The Finger On You                   | 0.99      | Standard      |
| 7       | Let's Get It Up                         | 0.99      | Standard      |
| 8       | Inject The Venom                        | 0.99      | Standard      |
| 9       | Snowballed                              | 0.99      | Standard      |
| 10      | Evil Walks                              | 0.99      | Standard      |

### 5. Накопительный итог продаж
| InvoiceId | InvoiceDate           | Total  | CumulativeTotal |
|-----------|-----------------------|--------|-----------------|
| 1         | 2009-01-01 00:00:00   | 1.98   | 1.98            |
| 2         | 2009-01-02 00:00:00   | 3.96   | 5.94            |
| 3         | 2009-01-03 00:00:00   | 5.94   | 11.88           |
| 4         | 2009-01-06 00:00:00   | 8.91   | 20.79           |
| 5         | 2009-01-11 00:00:00   | 13.86  | 34.65           |
| 6         | 2009-01-19 00:00:00   | 0.99   | 35.64           |
| 7         | 2009-02-01 00:00:00   | 1.98   | 37.62           |
| 8         | 2009-02-01 00:00:00   | 1.98   | 39.60           |
| 9         | 2009-02-02 00:00:00   | 3.96   | 43.56           |
| 10        | 2009-02-03 00:00:00   | 5.94   | 49.50           |
| 11        | 2009-02-06 00:00:00   | 8.91   | 58.41           |
| 12        | 2009-02-11 00:00:00   | 13.86  | 72.27           |
| 13        | 2009-02-19 00:00:00   | 0.99   | 73.26           |
| 14        | 2009-03-04 00:00:00   | 1.98   | 75.24           |
| 15        | 2009-03-04 00:00:00   | 1.98   | 77.22           |
