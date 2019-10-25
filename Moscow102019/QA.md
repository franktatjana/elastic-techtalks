## Here is the Q&A of the meetup in Moscow on 17.10.2019
### Q: Почему убрали типы? Что будет вместо них? Будут ли группы индексов?
A: Насчет типов убрали потому что поняли что это ошибка дизайна
Вот более подробная статья https://www.elastic.co/guide/en/elasticsearch/reference/master/removal-of-types.html
and https://github.com/elastic/infra/issues/10125
В этой статье также показано как можно иммитировать типы когда надо, например добавить custom field for type

### Насколько хороши стандартные анализаторы? Для русского imotov плагин явно лучше стандартного работает
* A: Igor Motov .... работал. я его больше не поддерживаю и перевожу всех на hunspell


### Как относитесь к pelias? Планируете сотрудничать?
* A: sadly no, but we still really really want it!

