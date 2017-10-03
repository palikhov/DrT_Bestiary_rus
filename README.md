# DnD_Monsters_rus

Список монстров из **Monster Manual** D&D5 и **Volo's Guide to Monsters** на русском языке.

Монстров можно фильтровать по:

 - названию

 - уровню опасности

 - типу и подтипу

 - размеру

 - источнику

 https://tentaculus.ru/monsters/

# Техническая информация

Данные монстров лежат в файле data/monsters.js в переменной allMonsters в формате JSON (https://ru.wikipedia.org/wiki/JSON)

Каждый монстр - один из объектов массива.

Большинство полей текстовые - что написано в базе, то и выводится на страницу. Но есть несколько исключений для фиксированных наборов значений:

 -  size (размер монстра) - одно из следующих значений: T, S, M, L, H, G - переводится в  соответственно: Крошечный, Маленький, Средний, Большой, Огромный, Колоссальный
 -  source (источник, откуда монстр взят) - пока два значения: MM и VGtM, соответственно: "Monsters Manual + Bungeon Master Guide" и "Volo's Guide to Monsters"

Кроме того, есть массивы объектов. Массивы заключены в квадратные скобки. кажддый объект заключен в фигурные скобки. Элементы массива (в данном случае элементы это объекты), разделяются заптыми. Пробелы, переносы не учитываются. Схематично так:

`[{},{},{}]`

или так

`[ {}, {},    {}  ]`


или так

```
[
  {},
  {},

  {}
]
```

В объекте находятся данные, представленные парой "ключ - значение". По ключу данные выбираются, значение отдается пользователю, если вкратце. Ключ должен быть на английском языке, в двойных кавычках и, желательно, осмысленным. Значение может быть тех простых типов - трока: "Аболет (Aboleth)", число: 20, булево: true и двух "сложных" - массив: [1,2,3], объект - {key: "value1", key2: "value42"}. Стока должна обязательно быть в двойных кавычках. Число и булева величина может быть без кавычек (по хорошему, они _должны_ быть без кавычек).

Значения ключей фиксированные, т.е. если будет опечатка, или добавится новый ключ, это не будет распознано программой.

Пример простейшего объекта:


```
{
  "name": "Aboleth"
}
```

 - name - ключ
 - Aboleth - значение

 Пары ключ-значение отделяются друг от друга запятыми, как и элементы в массиве.

```
{
  "name": "Aboleth",
  "languages": "Глубинная речь, телепатия 24 клетки"
}
```


Простой массив простых монстров:


```
[
  {
    "name": "Чук",
    "languages": "Голос разума"
  },
  {
    "name": "Гек",
    "languages": "Остальные голоса"
  }
]
```


Черты (traits) монстров обычно в массивы помещаются, ибо несть им числа. Выгядит сие образом соответственным:



```
[
  {
    "name": "Чук",
    "languages": "Голос разума",
    "trait": [
          {
            "name": "Шалун",
            "text": "Может шалить без зазрения совести"
          }
    ]
  },
  {
    "name": "Гек",
    "languages": "Остальные голоса"
  }
]
```

Это был массив trait с одним элементом, а вот с двумя:

```
[
  {
    "name": "Чук",
    "languages": "Голос разума",
    "trait": [
          {
            "name": "Шалун",
            "text": "Может шалить без зазрения совести"
          },
          {
            "name": "Умник",
            "text": "Хороо учится"
          }
    ]
  },
  {
    "name": "Гек",
    "languages": "Остальные голоса"
  }
]
```
