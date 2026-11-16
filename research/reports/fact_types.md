# Типы фактов и структура каждого типа

## 1) Milestone

```json
{
    "subject_type": "player",
    "subject_id": 130932, 
    "stat": "games", 
    "scope": "team", 
    "period": null,
    "team_id": 1245, 
    "current_value": 1508,
    "threshold": 1500
}
```

- `subject_type` (text) - player / team / coach


- `subject_id` (int) 


- `stat` (text):
  - games
  - wins
  - points
  - seasons 
  - остальные ??


- `scope` (text) - team / league 


- `period` (text) - season / career 


- `team_id` (int)


- `current_value` (int)


- `threshold` (int) - если был преодолёл **крупный** рубеж (100/500/1000) и нужно указать и **актуальное** и сам **рубеж** (1508 и 1500) 

---

## 2) Streak

```json
{
    "subject_type": "player",
    "subject_id": 130932, 
    "team_id": 1245,
    "length": 5, 
    "status": "active", 
    "streak_type": "losses",
    "where": "both",
    "cnt": 1,
    "opponent_type": "team",
    "opponent_id": 3059
}
```

- `subject_type` (text) - player / team / coach


- `subject_id` (int) 


- `team_id` (int) 


- `length` (int) - продолжительность


- `status` (text) - active / broken


- `streak_type` (text):
  - wins
  - losses
  - double_doubles


- `where` (text) - home / away / both


- `cnt` (int) - сколько раз такой страйк случался раньше (1 => впервые)


- `opponent_type` (text) 


- `opponent_id` (int)

---

## 3) Rivalry

```json
{
    "a": "Loko",
    "b": "Perm", 
    "wins_a": 19, 
    "wins_b": 3,
    "scope": null,
    "period": "season"
}
```

- `a` (text) - Оппонент 1


- `b` (text) - Оппонент 2


- `wins_a` (int) - Победы у первого


- `wins_b` (int) - Победы у 2


- `scope` (text) - team / league 


- `period` (text) - season / career / null (за все время)


## 4) Player Record → Record

```json
{
    "stat": "rebounds",
    "period": "career",
    "scope": null,
    "value": 12, 
    "cnt": null, 
    "subject_id": 91854,
    "subject_type": "player",
    "team_id": 48854
}
```

- `stat` (text) - Тип статистики у рекорда
  - points
  - rebounds
  - efficiency
  - остальные (какие-нибудь командные) ??


- `period` (text) - season / career / null (за все время)


- `scope` (text) - league / team


- `value` (int) - Значение рекорда


- `cnt` (int) - Кол-во раз когда рекорд выполнялся (если 1 то впервые)


- `subject_id` (int) 


- `subject_type` (text) - player / coach / team  


- `team_id` (int)

---

## 5) Roster Event

```json
{
    "subject_id": 1123,
    "team_id": 62343,
    "subject_type": "player", 
    "event_type": "debut", 
    "scope": null,
    "period": "career",
    "former_team_id": 8392,
    "cnt": 1
}
```

- `period` (text) - season / career / null (за все время)


- `scope` (text) - league / team


- `event_type` (text) - debut / vs_former_team / return / first_start ?? / absent


- `cnt` (int) - Кол-во раз когда рекорд выполнялся (если 1 то впервые)


- `subject_id` (int) 


- `subject_type` (text) - player / coach / team  


- `team_id` (int)


- `former_team_id` (int)


- `cnt` (int) - Кол-во раз когда случалось событие (1 => впервые)

---

## 6) Stat Count


```json
{
    "subject_type": "player",
    "subject_id": 130932, 
    "stat": "games", 
    "scope": "team", 
    "period": "season",
    "team_id": 1245, 
    "current_value": 1508,
    "cnt": 2,
    "opponent_id": 1234
}
```

- `subject_type` (text) - player / team / coach


- `subject_id` (int) 


- `stat` (text):
  - games
  - wins
  - points
  - assists 
  - остальные ??


- `scope` (text) - team / league


- `period` (text) - season / career 


- `team_id` (int)


- `current_value` (int)


- `cnt` (int) - Кол-во раз когда такая статистика набиралась (1 => впервые)


- `opponent_id` (int)

---

## 7) Double Double

```json
{
    "subject_id": 130932, 
    "points": 13, 
    "rebounds": 23, 
    "assists": 2,
    "steals": 5,
    "blocks": 1,
    "team_id": 1245,
    "opponent_id": 1234
}
```

- `subject_id` (int) 


- `points` (int) - очки 


- `rebounds` (int) - подборы


- `assists` (int) - передачи


- `steals` (int) - перехваты


- `blocks` (int) - блокированные броски 


- `team_id` (int)


- `opponent_id` (int)


---

### ⚠️ Удаление / добавление типов:

- ❌ Удаляем `standout_performance` -> он теперь входит в `Stat Count`


