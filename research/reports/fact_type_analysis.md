# Анализ существующих типов:

## 1) Milestone

### Поля этого типа:

<img width="793" height="168" src="pics/milestone.png" />


### Поле stat:

#### Уникальные значения

<img width="273" height="220" src="pics/fact_types.png" />

<img width="989" height="208" src="pics/fact_types_n.png" />

#### Примеры для `game`

##### 1) Тренер и команда 

**Факт:**

Evgeny Pashutin played his 127th game with BETCITY PARMA, making the Perm team the first in the Russian coach’s career in number of games, overtaking UNICS (126).

**Идея:** 

Подсчет числа игр в качестве тренера с определенной командой

**Какие поля:** 

- `Субъект` - тренер
- `Название субъекта` - Evgeny Pashutin
- `Объект` - игры
- `Кол-во объектов` - 127
- `Масштаб` - команда
- `Название масштаба` - BETCITY PARMA
- `Команда` - BETCITY PARMA

**Сравнение:**

Мы берем два факта
1) Старый - Тренер Evgeny Pashutin провел 126 игр с командой UNICS
2) Новый - Тренер Evgeny Pashutin провел 127 игр с командой BETCITY PARMA

**Claim от преподавателя:**

{"stat": "games", "scope": "team", "threshold": 127, "subject_id": 130931, "current_value": 127}

**Мое предположение:**

{"subject": "coach", "subject_id": 130931, "stat": "games", "scope": "team", "team_id": 1234, "current_value": 127}

И потом сравниваем два одинаковых факта? Поэтому milestone?

##### 2) Тренер и команда 

**Факт:**

Vladislav Konovalov has played his 30th game as head coach of Samara and has only won 2 games so far.

**Идея:** 

Тренер сыграл 30 игр в качестве тренера команды и выиграл всего 2 

**Какие поля:** 

- `Субъект` - тренер
- `Название субъекта` - Vladislav Konovalov
- `Объект` - игры
- `Кол-во объектов` - 30
- `Масштаб` - команда
- `Название масштаба` - Samara
- `Команда` - Samara


- `Субъект` - тренер
- `Название субъекта` - Vladislav Konovalov
- `Объект` - победы
- `Кол-во объектов` - 2
- `Масштаб` - команда
- `Название масштаба` - Samara
- `Команда` - Samara

**Сравнение:**

Мы берем два факта
1) Много - Тренер Vladislav Konovalov провел 30 игр с командой Samara 
2) Мало - Тренер Vladislav Konovalov выиграл 2 игры с командой Samara (эту пока не трогаем, это stat win)

**Claim от преподавателя:**

{"stat": "games", "scope": "team", "threshold": 30, "current_value": 30}

**Мое предположение:**

{"subject": "coach", "subject_id": 130931, "stat": "games", "scope": "team", "team_id": 1234, "current_value": 30}

и как доп:

{"subject": "coach", "subject_id": 130931, "stat": "wins", "scope": "team", "team_id": 1234, "current_value": 2}

Потом их связываем через другие поля


##### 3) Игрок и матч в лиге 

**Факт:**

Today’s game was a milestone for two Enisey players. Dmitry Sonko played his 100th game in the VTB League (all for Enisey). Artem Antipov has played 50 games.

**Идея:** 

Игрок сыграл сколько-то игр в лиге.

**Какие поля:** 

- `Субъект` - игрок
- `Название субъекта` - Dmitry Sonko
- `Объект` - игры
- `Кол-во объектов` - 100
- `Масштаб` - лига
- `Название масштаба` - VTB League
- `Команда` - Enisey


- `Субъект` - игрок
- `Название субъекта` - Artem Antipov
- `Объект` - игры
- `Кол-во объектов` - 50
- `Масштаб` - лига
- `Название масштаба` - VTB League
- `Команда` - 

**Сравнение:**

Мы берем два одинаковых факта для одной команды

**Claim от преподавателя:**

{"stat": "games", "scope": "league", "threshold": 100, "current_value": 100}

**Мое предположение:**

{"subject": "player", "subject_id": 130931, "stat": "games", "scope": "league", "team_id": 1234, "current_value": 100}

{"subject": "player", "subject_id": 130932, "stat": "games", "scope": "league", "team_id": null, "current_value": 50}

##### 4) Игрок и матч в лиге 

**Факт:**

Aleksandr Zakharov played his 100th game in the VTB United League. He has played 49 games in the League for BETCITY PARMA.

*Идея:** 

Игрок сыграл сколько-то игр в лиге. Сколько-то за одну команду

**Какие поля:** 

- `Субъект` - игрок
- `Название субъекта` - Aleksandr Zakharov
- `Объект` - игры
- `Кол-во объектов` - 100
- `Масштаб` - лига
- `Название масштаба` - VTB League
- `Команда` - 


- `Субъект` - игрок
- `Название субъекта` - Aleksandr Zakharov
- `Объект` - игры
- `Кол-во объектов` - 49
- `Масштаб` - команда
- `Название масштаба` - BETCITY PARMA
- `Команда` - BETCITY PARMA

**Сравнение:**

Мы берем два факта про одного игрока

**Claim от преподавателя:**

{"stat": "games", "scope": "league", "threshold": 100, "current_value": 100}

**Мое предположение:**

{"subject": "player", "subject_id": 130931, "stat": "games", "scope": "league", "team_id": null, "current_value": 100}

{"subject": "player", "subject_id": 130932, "stat": "games", "scope": "team", "team_id": 1245, "current_value": 49}

##### ИТОГО ДЛЯ GAME 

```
{
    "subject": "player",
    "subject_id": 130932, 
    "stat": "games", 
    "scope": "team", 
    "team_id": 1245, 
    "current_value": 49
}
```

#### Примеры для `total_points`

##### 1) Игрок и кол-во очков в лиге 

**Факт:**

Nikita Mikhailovskii (25) scored 1,000 points in his VTB League career.

**Идея:** 

Игрок набрал сколько-то очков в лиге. (круглое число)

**Какие поля:** 

- `Субъект` - игрок
- `Название субъекта` - Nikita Mikhailovskii
- `Объект` - очки
- `Кол-во объектов` - 1000
- `Масштаб` - карьера
- `Название масштаба` - null
- `Команда` - null

**Сравнение:** no

**Claim от преподавателя:**

{"stat": "total_points", "scope": "career", "threshold": 1000, "current_value": 1000}

**Мое предположение:**

`{"subject": "player", "subject_id": 130931, "stat": "total_points", "scope": "career", "team_id": null, "current_value": 1000}`

или если убираем subject то остается 

`{"subject_id": 130931, "stat": "total_points", "scope": "career", "team_id": null, "current_value": 1000}`

##### 2) Игрок и кол-во очков в лиге 

**Факт:**

Ilia Popov scored 1,500th point in the VTB League. Lokomotiv Kuban center currently has 1,508 points.

**Идея:** 

Игрок набрал 1500 очков в лиге. Сейчас у него 1508

**Какие поля:** 

- `Субъект` - игрок
- `Название субъекта` - Ilia Popov
- `Объект` - очки
- `Кол-во объектов` - 1508
- `Масштаб` - карьера
- `Название масштаба` - null
- `Команда` - null
- `Рубеж` - 1500

**Сравнение:** no

**Claim от преподавателя:**

{"stat": "total_points", "scope": "league", "threshold": 1500, "subject_id": 24712, "current_value": 1508}

**Мое предположение:**

`{"subject_type": "player", "subject_id": 130931, "stat": "total_points", "scope": "career", "team_id": null, "current_value": 1508, "threshold": 1500}`

##### 3) Игрок набрал юбилейное кол-во очков

**Факт:**

Maksim Barashkov surpassed 1,000 points in his VTB League career.

**Идея:** 

Игрок набрал 1000 очков в лиге.

**Какие поля:** 

- `Субъект` - игрок
- `Название субъекта` - Maksim Barashkov
- `Объект` - очки
- `Кол-во объектов` - null
- `Масштаб` - карьера
- `Название масштаба` - null
- `Команда` - null
- `Рубеж` - 1000

**Claim от преподавателя:**

{"rank": null, "stat": "total_points", "scope": "career", "threshold": 1000, "current_value": 1000}

**Мое предположение:**

`{"subject_type": "player", "subject_id": 130931, "stat": "total_points", "scope": "career", "team_id": null, "current_value": null, "threshold": 1000}`

##### ИТОГО ДЛЯ TOTAL_POINTS 

```
{
    "subject_type": "player",
    "subject_id": 130932, 
    "stat": "games", 
    "scope": "career", 
    "team_id": 1245, 
    "current_value": null,
    "threshold": 1000
}
```

#### Примеры для `wins`

##### Первая победа в качестве тренера

**Факт:**

Today’s win was the first in Anton Yudin’s career as head coach of the VTB League team.

**Идея:** 

Тренер одержал первую победу в карьере как тренер.

**Какие поля:** 

- `Субъект` - тренер
- `Название субъекта` - Anton Yudin
- `Объект` - победы
- `Кол-во объектов` - 1
- `Масштаб` - карьера
- `Название масштаба` - null
- `Команда` - null
- `Рубеж` - 1

**Claim от преподавателя:**

{"stat": "wins", "scope": "career", "threshold": 1, "subject_id": 131047, "current_value": 1}

**Мое предположение:**

`{"subject_type": "coach", "subject_id": 130931, "stat": "wins", "scope": "career", "team_id": null, "current_value": 1, "threshold": 1}`


#### Примеры для `seasons`

##### Команда открыла свой 10 тый сезон в лиге

**Факт:**

The game was a milestone for both teams. BETCITY PARMA opened its 10th season in the VTB League, while UNICS won its first game for the 10th time in a row.

**Идея:** 

Команда открыла свой 10 тый сезон в лиге

**Какие поля:** 

- `Субъект` - команда
- `Название субъекта` - BETCITY PARMA
- `Объект` - seasons
- `Кол-во объектов` - 10
- `Масштаб` - league
- `Название масштаба` - VTB League
- `Команда` - BETCITY PARMA
- `Рубеж` - 10

**Claim от преподавателя:**

{"stat": "seasons", "scope": "league", "threshold": 10, "subject_id": 3059, "current_value": 10}

**Мое предположение:**

`{"subject_type": "team", "subject_id": 130931, "stat": "seasons", "scope": "league", "team_id": 130931, "current_value": 10, "threshold": 10}`

##### ИТОГО 

```
{
    "subject_type": "player",
    "subject_id": 130932, 
    "stat": "games", 
    "scope": "team", 
    "team_id": 1245, 
    "current_value": 49,
    "threshold": 1
}
```

---

## 2) Streak

### Поля этого типа:

<img width="793" height="168" src="pics/streak.png" />


### Мои предположения

```
{
    "subject_type": "player",
    "subject_id": 130932, 
    "team_id": 1245,
    "length": 5, 
    "status": "active", 
    "streak_type": "losses",
    "cnt": 1
    "opponent_type": "team",
    "opponent_id": 3059
}
```

#### Примеры 

##### 1) Команда впервые проиграла 3 игры подряд

**Факт:**

For the first time in the history, Samara started the season with 3 consecutive losses.

**Идея:** 

Команда начала сезон с 3 поражений подряд

**Какие поля:** 

- `Субъект` - команда
- `Название субъекта` - Samara
- `Длина` - 3
- `Статус` - не прерван
- `Тип` - поражения
- `Кол-во раз` - 1
- `Команда` - 


**Claim от преподавателя:**

{"length": 3, "status": "active", "subject_id": 2792, "streak_type": "losses"}

**Мое предположение:**

{"subject_type": "team", "subject_id": 130931, "team_id": 1245, "length": 3, "status": "active", "streak_type": "h2hlosses", "cnt": 1}

##### 2) Одна команды выиграла 16 игр подряд у второй

**Факт:**

Zenit extended its winning streak versus the Perm team to 16 in a row (26-3 overall).

**Идея:** 

Одна команды выиграла 16 игр подряд у второй ????????????????????????????????

**Какие поля:** 

- `Субъект` - команда
- `Название субъекта` - Zenit
- `Длина` - 16
- `Статус` - не прерван
- `Тип` - победы ????????????????? 
- `Впервые` - null
- `Команда` - Zenit
- `Тип соперника` - команда
- `Соперник` - Perm


**Claim от преподавателя:**

{"length": 16, "status": "active", "subject_id": 2994, "opponent_id": 3059, "streak_type": "h2h_wins"}

**Мое предположение:**

{"subject_type": "team", "subject_id": 130931, "team_id": 1245, "length": 16, "status": "active", "streak_type": "?", "cnt": null,  "opponent_type": "team",  "opponent_id": 3059}

##### 3) Одна команды выиграла последние 3 игр подряд у второй

**Факт:**

Rivalry history score: 11-4, MBA-MAI leads. The previous 3 games were won by the guests.

**Идея:** 

Одна команды выиграла последние 3 игр подряд у второй

**Какие поля:** 

- `Субъект` - команда
- `Название субъекта` - MBA-MAI
- `Длина` - 3
- `Статус` - не прерван
- `Тип` - победы 
- `Впервые` - null
- `Команда` - MBA-MAI
- `Тип соперника` - команда
- `Соперник` - Пари Нижний Новгород


**Claim от преподавателя:**

{"length": 3, "status": "active", "subject_id": 468, "opponent_id": 2747, "streak_type": "h2h_wins"}

**Мое предположение:**

{"subject_type": "team", "subject_id": 130931, "team_id": 1245, "length": 3, "status": "active", "streak_type": "h2hwins", "cnt": null, "opponent_type": "team", "opponent_id": 3059}


##### 4) Тип double-double

**Факт:**

Terrell Carter recorded his second consecutive double-double with 12 points and 11 rebounds.

**Идея:** 


**Какие поля:** 

- `Субъект` - игрок
- `Название субъекта` - Terrell Carter
- `Длина` - 2
- `Статус` - не прерван
- `Тип` - double-double 
- `Впервые` - null
- `Команда` - null
- `Тип соперника` - null
- `Соперник` - null 

---


## 3) Rivalry

### Поля этого типа:

<img height="168" src="pics/rivalry.png" />

##### 1) Счет встреч двух команд

**Факт:**

After 5 losses in a row, Perm team finally broke losing streak against the Moscow team.
**The current rivalry history score is 19-3, CSKA leads.**

**Идея:** 

Соперничество между двумя командами счет 19-3

**Какие поля:** 

- `Соперник 1` - CSKA
- `Соперник 2` - Perm
- `Победы у 1` - 19
- `Победы у 2` - 3

**Claim от преподавателя:**

{"leader": "CSKA", "wins_a": 19, "wins_b": 3}

**Мое предположение:**

{"a": "CSKA", "b": "Perm", "wins_a": 19, "wins_b": 3}


##### 2) Ошибка классификации

**Факт:**

PARMA surpassed Samara in head-to-head wins (6-5).

**Идея:** 

НЕ rivalry А standings_change


##### 3) Сравнение счета 

**Факт:**

**Enisey ties rivalry history score with Pari NN. 
The teams now have 14 wins each.** 
`The last time Krasnoyarsk team won in Nizhny Novgorod in December 2023. - отсюда факт не достается`

**Идея:** 

Сравнение счета в соперничестве 

**Какие поля:** 

- `Соперник 1` - Enisey
- `Соперник 2` - Pari NN
- `Победы у 1` - 14
- `Победы у 2` - 14

**Claim от преподавателя:**

{"leader": "tie", "wins_a": 14, "wins_b": 14}

**Мое предположение:**

{"a": "Enisey", "b": "Pari NN", "wins_a": 14, "wins_b": 14}


##### 4) Одна команда ведет

**Факт:**

The rivalry history score is 44-4, CSKA leads.

**Идея:** 

Одна команда ведет

**Какие поля:** 

- `Соперник 1` - CSKA
- `Соперник 2` - null
- `Победы у 1` - 44
- `Победы у 2` - 4

**Claim от преподавателя:**

{"leader": "CSKA", "wins_a": 44, "wins_b": 4, "team_a_id": 15, "team_b_id": 468}

**Мое предположение:**

{"a": "CSKA", "b": null, "wins_a": 44, "wins_b": 4, "scope": null}

---


## 4) Player Record

### Поля этого типа:

<img width="793" height="168" src="pics/player_record.png" />


##### 1) Рекорд по rebounds

**Факт:**

In his debut game for Enisey, **Egor Ryzhov set a new career-high rebounds** and recorded his 
first double-double in the VTB League **with** 12 points and **12 rebounds**.

**Идея:** 

Рекорд по rebounds

**Какие поля:** 

- `Кто` - Egor Ryzhov
- `Тип статистики` - rebounds
- `Значение` - 12
- `Масштаб` - career
- `Кол-во раз когда повторялся рекорд` - null

**Claim от преподавателя:**

{"stat": "rebounds", "scope": "career", "value": 12, "is_tied": false, "subject_id": 91854}

**Мое предположение:**

{"stat": "rebounds", "scope": "career", "value": 12, "cnt": null, "subject_id": 91854}


##### 2) Рекорд за команду

**Факт:**

Luka Samanic had his best scoring and efficient game for Zenit—23 points and 37 effort. points.

**Идея:** 

Первые double-double

**Какие поля:** 

- `Кто` - Luka Samanic
- `Тип статистики` - efficiency
- `Значение` - 37
- `Масштаб` - team
- `Кол-во раз когда повторялся рекорд` - null

**Claim от преподавателя:**

{"stat": "efficiency", "scope": "season", "value": 37, "is_tied": false, "subject_id": 515688}

**Мое предположение:**

{"stat": "efficiency", "scope": "team", "value": 37, "cnt": null, "subject_id": 91854}


---


## 5) Roster Event

### Поля этого типа:

<img width="793" height="168" src="pics/roster_event.png" />


##### 1) Дебют

**Факт:**

**In his debut game for Enisey**, Egor Ryzhov set a new career-high rebounds and recorded 
his first double-double in the VTB League with 12 points and 12 rebounds.

**Идея:** 

Дебют

**Claim от преподавателя:**

{"team_id": 688, "event_type": "debut", "subject_id": 91854}

**Мое предположение:**

{"subject_id": 688, "team_id": 688, "subject_type": "player", "event_type": "debut", "scope": "career"}


##### 2) Против бывшей команды

**Факт:**

4 Loko players are now playing for Enisey: Mikhail Vedishchev, Nikita Evdokimov, 
Alexey Sereda and Sergey Dolinin.

**Claim от преподавателя:**

{"team_id": 688, "event_type": "vs_former_team", "subject_id": 44632}

**Мое предположение:**

{"subject_id": 44632, "team_id": 688, "subject_type": "player", "event_type": "vs_former_team", "scope": null, "former_team_id": 8473}

###### Еще один 

**Факт:**

This was Daniil Kasatkin’s first game against his former team.

**Claim от преподавателя:**

{"team_id": 688, "event_type": "vs_former_team", "subject_id": 26909}

**Мое предположение:**

{"subject_id": 44632, "team_id": 688, "subject_type": "player", "event_type": "vs_former_team", "scope": null, "former_team_id": 8473, "cnt": 1}


##### 3) Возвращение

**Факт:**

**Jeremiah Martin has recovered from injury and returned.** Today’s game was only the second of the season for the guard. 
He scored 13 points in 12 minutes.

**Claim от преподавателя:**

{"team_id": 2650, "event_type": "return", "subject_id": 393326}

**Мое предположение:**

{"subject_id": 44632, "team_id": 688, "subject_type": "player", "event_type": "return", "scope": null, "former_team_id": null}

##### 4) first_start

**Факт:**

MBA-MAI-Junior guard Matvey Padius was named the MVP of October in the Youth League. 
**He made debut for the starting lineup in this game.**


**Claim от преподавателя:**

{"subject_type": "player", "event_type": "first_start", "subject_id": 125506, "team_id": 2747}

**Мое предположение:**

{"subject_id": 44632, "team_id": 688, "subject_type": "player", "event_type": "return", "scope": null, "former_team_id": null}

---

## 6) Season Count

### Поля этого типа:

<img width="793" height="168" src="pics/season_count.png" />


##### 1) first_start

**Факт:**

MBA-MAI-Junior guard Matvey Padius was named the MVP of October in the Youth League. 
**He made debut for the starting lineup in this game.**

**Claim от преподавателя:**

{"subject_type": "player", "event_type": "first_start", "subject_id": 125506, "team_id": 2747}

**Мое предположение:**

{"subject_id": 44632, "team_id": 688, "subject_type": "player", "event_type": "return", "scope": null, "former_team_id": null}



---

## Other 

### 1) Почти рекорд

The Kazan team was close to setting a record for the first days of the VTB League, scoring 103 points. 
The record for scoring belongs to the same UNICS of 2016/17 season (104 points).


UNICS scored 103 points, one short of the League record for season-opening games (104 by UNICS in 2016/17).

**Мое предположение:**

1) Берем для рекорда тип Record


```json
{
    "stat": "scoring",
    "period": "season",
    "scope": "league",
    "value": 104, 
    "cnt": null, 
    "subject_id": 91854,
    "subject_type": "team",
    "team_id": 91854
}
```

И добавляем второй тип "Почти рекорд"

2) Меняем тип рекорд (если curr_value < value => почти рекорд

```json
{
    "stat": "scoring",
    "period": "season",
    "scope": "league",
    "value": 104, 
    "curr_value": 103, 
    "cnt": null, 
    "subject_id": 91854,
    "subject_type": "team",
    "team_id": 91854
}
```

### 2) 10 подряд победа в первом матче сезона

UNICS won its first game for the 10th time in a row.

**Мое предположение:**

Берем тип Streak

```json
{
    "subject_type": "team",
    "subject_id": 130932, 
    "team_id": 130932,
    "length": 10, 
    "status": "active", 
    "streak_type": "first_game_win",
    "where": "both",
    "cnt": null,
    "opponent_type": null,
    "opponent_id": null
}
```

### 3) Нет игроков 

Loko was without Jeremiah Martin, Kirill Elatontsev and Vsevolod Ishchenko.


**Мое предположение:**

Берем тип Roster Event

```json
{
    "subject_id": 1123,
    "team_id": 62343,
    "subject_type": "player", 
    "event_type": "absent", 
    "scope": null,
    "period": null,
    "former_team_id": null,
    "cnt": null
}
```






