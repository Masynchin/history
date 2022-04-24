# История моих репозиториев

Здесь рассказывается о всех моих проектах - мотивация к созданию, их поддержка, обновление.

## [assistypes](https://github.com/Masynchin/assistypes) (2020.08.06)

Мой первый репозиторий.

Увидев метод `.resize()` массивов numpy, я решил повторить это для стандартного списка.
В `StructuredList` я смог это реализовать, и он стал основой (и долгое время единственным классом) пакета assistypes.

Позже были добавлены ещё несколько классов, но после пакет перестал мною поддерживаться.

## [CheWeatherBot](https://github.com/Masynchin/CheWeatherBot) (~2020.12.20)

Телеграм-бот для погоды моего родного города - Череповца.

У меня уже был небольшой опыт написания ботов (один для ВК), так что решившись писать их для ТГ, я решил изучить что-то новое.
Выбор пал на асинхронность, поэтому в качестве основы был выбран [aiogram](https://github.com/aiogram/aiogram)
(немалую роль в выборе сыграло и [это видео](https://www.youtube.com/watch?v=Kh16iosOTIQ)).

В первой версии был использован aiogram для ТГ, aiohttp для запросов к погодному сервису, sqlite для хранения данных подписчиков рассылки,
и небольшая библиотека [loguru](https://github.com/loguru/loguru) для логирования.

## [CheWeatherBot](https://github.com/Masynchin/CheWeatherBot) 1.1 (2021.03.18-2021.04.27)

В качестве школьного проекта я решил выбрать `CheWeatherBot`, но с расширенным функционалом.

Вместо ручного парсинга JSON-ответа погодного сервера был использован [pydantic](https://github.com/samuelcolvin/pydantic).
С его помощью стало легче реализовать новые функции - получение погоды в конкретное время.

Бота я решил пристроить на heroku, чтобы я и другие люди могли им пользоваться в (почти) любое время.
Сначала под это была выделена новая ветвь с реализацией хранения данных в PostgreSQL (бесплатная БД на heroku)
через [psycopg2](https://github.com/psycopg/psycopg2). Спустя некоторое время я объединил хранение данных
с помощью [SQLAlchemy](https://github.com/sqlalchemy/sqlalchemy), и стало возможным удобно тестировать на собственном ноутбуке с SQLite,
а на heroku использовать PostgreSQL.

Спустя день после ввода SQLAlchemy в проект произошёл переход с синхронного на ассинхронный сервис хранения данных подписчиков рассылки.
Проект стал полностью асинхронным.

Тут же были применены и менее заметные улучшения - создание отдельной папки под .py файлы, написание докстрингов.

## [SYB](https://github.com/fuetser/flask_project) (2021.02.19-2021.04.24)

Итоговый проект в курсе Яндекс.Лицея.

Вместе с Сашей [@fuetser](https://github.com/fuetser) Захаручком нам предстояло выполнить проект на flask-стаке ([flask](https://github.com/pallets/flask), [flask-sqlalchemy](https://github.com/pallets/flask-sqlalchemy), [flask-restful](https://github.com/flask-restful/flask-restful)) + Bootstrap5.
Мы решили создать что-то наподобие реддита, и за два месяца смогли создать приложение с аутентификацией, категоризацией, публикацией...

Мы смогли реализовать базовые концепции соц.сетей - аккаунты, публикации, комментарии, лайки, поиск. Помимо основной работы над бекендом, Саша сильно помог с JS.
Моей же сверх-задачей были модели данных, создание и взаимодействие над ними (получение постов из подписок пользователя, алгоритм сортировки постов по нашей
системы оценок и т.д.).

Это был мой первый веб-проект и первое фулстак-приложение.

## [Tasker](https://github.com/Masynchin/tasker) (2021.05.12-2021.05.18)

Сразу после сдачи проекта для Яндекс.Лицея я захотел написал своё собственное веб-приложение.
В качестве идеи был выбран сам Яндекс.Лицей - площадка с курсами>задачами>уроками по программированию.

Изучая документацию aiohttp я заметил, что на нём можно писать не только клиентскую часть, но и серверную. Беря во внимание структуры предудыщего проекта,
я стал искать схожие компоненты - шаблонизацию ([aiohttp-jinja2](https://github.com/aio-libs/aiohttp-jinja2)),
сессии ([aiohttp-sessions](https://github.com/aio-libs/aiohttp-session))
и асинхронную ORM ([TortoiseORM](https://github.com/tortoise/tortoise-orm)).

За 60 часов в течение недели была создана рабочая версия.

## [CheWeatherBot](https://github.com/Masynchin/CheWeatherBot) 1.2 (2021.07.18-2021.07.19)

После работы над другими проектами, я вернулся с небольшими исправлениями и техническими нововведениями.

Были добавлены [black](https://github.com/psf/black) и [flake8](https://github.com/PyCQA/flake8).
С их помощью код был немного почищен, а после улучшен более качественной документацией.

## [Tasker](https://github.com/Masynchin/tasker) 1.1 (2021.08.13-2021.09.01)

За три месяца после создания рабочей версии я узнал столько всего, что решил потратить всё своё время до начала учёбы на улучшение "Таскера".

С самого начала я видел места для рефакторинга, но не мог себе его позволить ввиду отсутствия тестов.

Я решил написать их, но для этого нужно было выполнить данный план:
- исправить стиль кода
- исправить незначительные огрехи кода
- подготовить архитектуру для тестирования

Введя pre-commit с моей базовой настройкой я начал исправить стиль кода. Была добавлена документация (увеличил строгость, теперь докстринги писались и к целым модулям),
единый формат кода, и были введены аннотации типов (перейдя с ST3 на VSCode, и попробовав работу со строго-типизированным языком,
я решил использовать их во всех следующих проектах).

Были исправлены огрехи разных калибров - начиная от замены if/elif на dict, заканчивая заменой метода маршрутизации проекта
с django-like таблицы путей на flask-like декораторы.

После этого я начал исправлять архитектуру приложения. Проблема была в том, что хоть и бизнес-сервисы были отделены от веб-хендлера,
в них была зависимость от aiohttp - передавались объекты запросов, форм и т.д. Исправив это, я написал тесты к сервисам (используя покрытие),
и благодаря этому улучшил часть запросов к БД, методы работы отдельных функций.

## [zif](https://github.com/Masynchin/zif) (2021.10.03-...)

Изначально Tasker должен был быть написан на Django+React (такой же стек использует Яндекс.Лицей), но получилось иначе.

В первой версии Tasker я увидел, какие моменты хотелось бы изменить (повторяющиеся запросы в БД для получения пользователя, повторение кода для компонентов на фронте),
и начал думать, как это можно исправить. Проекты [classroom](https://github.com/drdilyor/classroom) и [geekr](https://github.com/jarvis394/geekr) помогли мне понять,
как можно решить эти проблемы (и дали базу для нового кода).

Сразу же переделывать Tasker я не стал, а решил опробовать новые технологии на другом проекте - так и был создан zif. zif - это упрощённая версия Двача.
Хоть у меня и скептичное отношение к данному ресурсу, но в качестве базы проекта он мне хорошо подходит -
отсутствие аутентификации, переиспользование компонентов (комментариев), понятная структура API.

Тут я впервые сделал разделение на фронт и бэк. В SYB у нас уже была работа с CRUD-API, но это было сделано сбоку, здесь же это является основным способом связи
между Python-бэком и React-фронтом.

В каждом моём проекте есть какие-то новые сложности - в этом же, кроме освоения React, была проблема с БД.
Комментарии имееют иерархическую структуру, и чтобы одним запросом их получить, нужно использовать recursive-cte.
В моей любимой [TortoiseORM](https://github.com/tortoise/tortoise-orm) такого функционала не оказалось
([придумали будущий интерфейс](https://github.com/tortoise/tortoise-orm/issues/819), но реализации ещё нет).
Пришлось использовать синхронную [peewee](https://github.com/coleifer/peewee), которая схожа по интерфейсу.

## [ScheduleDrawer](https://github.com/Masynchin/ScheduleDrawer) (2021.12.12)

Мне нравится рассматривать разные языки, и я захотел изучить какой-нибудь подробнее. Среди языков с понятным синтаксисом я выбрал следующих кандидатов: Swift, Dart, Elixir (ещё был найден язык [Ballerina](https://github.com/ballerina-platform/ballerina-lang), но он не достаточно популярный). Swift и Dart не поддерживаются на моём ноутбуке, поэтому выбор пал на Elixir.

Прочитав [вводный курс](https://elixir-lang.org/getting-started/introduction.html) я решил применить язык на практике. Мне понравилась идея функционального подхода, для лучшего его понимания я решил не создавать что-то новое, а переделать существующий проект с другой парадигмой. Выбор пал на отрисовщик школьного расписания, готовые реализации есть как у меня (делал раньше бота для своей школы), так и у @BobaUbisoft17.

Сначала я выполнил абстрактную реализацию. Было трудно начать мыслить неизменяемыми структурами данных, но я всё-таки смог выполнить эту задачу. Мне очень понравился pipe-механизм, который заставляет структурировать код, преобразуя его в читаемые функции.

После этого мне хотелось проверить работоспособность кода. Я не смог найти библиотеку для работы с изображениями, которая могла бы на лету создавать изображения и высчитывать размер их сторон, что являлось необходимым для работы кода.

Этот проект помог мне в изучении основ Elixir, после чего я начал плотнее изучать стандартную библиотеку и применять новые знания для улучшения данной реализации.

## [Textode](https://github.com/Masynchin/textode) (2021.08.12-2022.01.29)

Textode разрабатывался специально под [проект](https://github.com/bullbesh/pfr_instruction) моего друга. Продукт его проекта - чат-бот в Telegram по пенсионным вопросам для сотрудников ПФР. Для интеграции в Telegram использовался [aiogram](https://github.com/aiogram/aiogram), и потому вся логика диалога описывалась с помощью хедлеров. Вкупе с докстрингами, сигнатурами функций и декораторами это выглядело [плохо](https://github.com/bullbesh/pfr_instruction/blob/e39734817b5203056b72a6800334bd3455b4169c/pfr_instruction/main.py) - сложно понять структуру диалога, добавить что-то новое. Именно это должна была решить моя библиотека.

Сначала я определил точную проблему, которыю должен решать Textode - построение бота, не имеющего состояния. Именно такого бота и делал мой друг - структура диалога задаётся наперёд, нет никаких изменяемых данных.

Теперь эту проблему нужно решить. Сама модель диалога похожа на дерево, которое выглядит как-то так:

~~~mermaid
graph TD;
    Начало -->|"Секция 1"| Диалог1;
    Начало -->|"Секция 2"| Диалог2;
    Начало -->|"Секция 3"| Диалог3;
~~~

Почему бы сразу не представить наш диалог в виде дерева? В этом и заключается идея Textode.

Оказалось, что преумещств у Textode больше, чем только помощь в написании логики диалога:

- Разделение диалога и его обёртки

Textode позволяет отделить логику диалога от логики представления. В случае чат-бота друга код разбивается на две части: сам диалог, и Telegram-оболочка вокруг него. В общем случае мы можем делать множество разных обёрток для одного диалога - представить его в виде чат-бота, текста в консоли, web-сайта и т.д. Так, например, к существующему диалогу чат-бота написать текстовую оболочку, и тестировать прямо из консоли, не запуская других процессов.

- Выделение структуры диалога

Так как мы вынесли всю логику в отдельный объект, мы можем легче ориентироваться в структуре диалога.

- Простота в измении

Вытекает из предыдущего пункта. Мы можем быстро найти, куда нужно добавить/изменить/удалить данные.

## [ndnt](https://github.com/Masynchin/ndnt) (2022.01.29)

Вдохновлённый [творчеством Егора Бугаенко](https://www.yegor256.com/tag/oop.html), я решил попробовать изученные техники. Это и послужило началом проекту.

Я нашёл проблему - измерение отступов в кодобазе. Разбил предметную область на следующие сущности - Файлы, Файл, Строки кода, Строка кода, Отступ строки кода, Средний отступ строк кода, Сводка по отступам. Оставалось только реализовать их в коде. На всё про всё ушёл день. Украсил выпуск пакета [постом на reddit](https://www.reddit.com/r/Python/comments/sikfe7/i_created_a_tool_for_inspecting_indents/).

## [portfolio](https://github.com/Masynchin/portfolio) (2022.02.16-2022.02.19)

Второе вступительное задание для курса Яндекс.Лицея по Django было сверстать сайт-портфолио.

### Условия задания

- Статика
- Никаких фреймворков
- Семантическая вёрстка
- Наличие тёмной темы
- Адаптивность
- Успешность прохождения [W3CValidator](https://validator.w3.org)

Интересное задание, единственное интересное из всего курса, но не об этом.

### Дизайн сайта

Самое сложное было разработать дизайн. Но я поступил хитро - просто скопировал сам дизайн Яндекс.Лицея:

- Главная страница сайта Яндекс.Лицея:

<img width="1440" alt="Главная страница сайта Яндекс.Лицея" src="https://user-images.githubusercontent.com/47028153/162555741-1fcf7cf6-afcc-4596-bc30-c657fb3fbfb4.png">

- Главная страница моего портфолио:

<img width="1440" alt="Главная страница моего портфолио" src="https://user-images.githubusercontent.com/47028153/162555757-5f8b3b27-8d6d-4071-bb35-6e918c62f795.png">

*В Safari какие-то проблемы со шрифтом логотипа, в оригинале это шрифт старого логотипа Яндекса*

Пришлось делать больше страниц (чтобы было несколько разделов), но это не было минусом. Больше рассказал про выполнение критериев, про себя, про моё виденье предстоящего курса (увы, не совпало с ожиданиями).

### Семантическая вёрстка

Очень понравилось работать с чистым HTML и CSS, особенно вместе с условием
"семантической вёрстки". Вначале поставил себе правило не использовать тег
`div`, и так и не нарушил его. Из-за этого получившийся код легко читать.
Пример DOM-дерева страницы со статьёй:

~~~html
<!DOCTYPE html>
<html lang="ru">
  <head>...</head>
  <body>
    <header>...</header>
    <main>
      <a class="crumbs" href="index.html">...</a>
      <article>
        <h1>Адаптивность</h1>
        <p>...</p>
        <p>...</p>
        <p>...</p>
      </article>
    </main>
    <aside id="menu" class="menu" hidden>...</aside>
    <footer>...</footer>
  </body>
</html>
~~~

Такой трюк стал возможен и из-за специфичного CSS. Стилизация элементов,
в основном, идёт по HTML-тегам, а не классам. Это видно на примере:
только у хлебных крошек и меню есть свой класс, у остальных элементов его нет.

### Github-Pages

Когда тестировал адаптивность под телефоны, было неудобно пользоваться инструментами
разработчика. Поэтому я решил прикрутить к портфолио github-pages. Условия позоволяли -
полностью статический сайт, готовый репозиторий. Так я сделал свой первый сайт на github-pages.

### Валидация

Ещё одна автоматизация - проверка на [W3CValidator](https://validator.w3.org).
Для этого я использовал [этот action](https://github.com/marketplace/actions/html5-validator).
А ещё добавил результат проверки в виде шильдика в README.

### Итоги

Организаторы зачли почти максимум за задание, отбор был пройден, курс был начат и досрочно покинут.
А сайт [так и работает](https://masynchin.github.io/portfolio/).

## [Textode](https://github.com/Masynchin/textode) 2 (2022.03.12)

Textode успешно решил поставленную проблему. С тех пор он добавлял новую функциональность (не меняя своей сути),
но в какой-то момент вылезла проблема - чтобы определить диалог нужно было писать [уродливый](https://github.com/Masynchin/textode/blob/8c16e72c849342652428ef68ffe6fd1887edefe7/examples/multi_node.py) код.
Непорядок.

Следующее обновление должно было решить эту проблему. Казалось, что оно будет небольшим,
но в итоге вылилось в обновление до версии 2.x. Сейчас объясню, почему так получилось.

### Причины

Все доводы также собраны в [пулл-реквесте](https://github.com/Masynchin/textode/pull/1) с обновлением.

Проблема заключалась в реализации `MultiNode`. Она сама и её дочерние узлы должны иметь
одинаковый заголовок. Почему? Всё из-за реализации `Node`. Каждая `Node` сама определяет
своё название. В случае с `MultiNode`, нам нужен только один заголовок - для `MultiNode`,
дочерним же узлам мы не хотим давать отдельные названия. Из-за этого приходилось передавать
одинаковое название как в `MultiNode`, так и в её дочерние узлы. То, что это правильно
работало, всего лишь особенность `NodeDict`.

### Решение

Решение оказалось интересным. Вместо того, чтобы узел сам определял своё название, родительский
узел сам должен определять связи (они же названия) со своими дочерними узлами. Это хорошо видно
на примере `KeyboardNode`.

- До:

~~~python
KeyboardNode(
    Text("Something interesting", ...),
    Text("Current time?", ...),
    Text("Help!", ...),
)
~~~

- После:

~~~python
KeyboardNode(
    "Something interesting": Text(...),
    "Current time?": Text(...),
    "Help!": Text(...),
)
~~~

Теперь `Node` не должна сама определять своё название.

### Реализация

Из всех подклассов `Node` убран аттрибут названия узла. В родительские узлы теперь передаётся
словарь из пар "название - узел". Поменялась и регистрация узлов. `NodeDict` стал не нужен,
и регистрация стала происходить через отдельную процедуру.

Из-за этих изменений была потеряна обратная совместимость. Зато внешний и внутренний код стал
чище - его количество уменьшилось. Побочные действия в виде `NodeDict` исчезли. Тестирование
стало легче.

## [ndnt](https://github.com/Masynchin/ndnt) (2022.04.20-2022.04.22)

Функционал почти не изменился, но было улучшено оформление проекта.
README стал подробнее, добавлены CHANGELOG (впервые для меня) и github-actions для тестов (тоже впервые).

### Подробный README

В README сделал отдельную секцию "Usage", в которой под каждую опцию `ndnt`'а выделен отдельный пункт.
Позаимстовал эту манеру у [README для fd](https://github.com/sharkdp/fd#fd) - одного из лучших CLI-инструментов.

### Первый CHANGELOG

[Семантическое версионирование](https://semver.org/spec/v2.0.0.html) поддерживалось с самого начала,
изменения между версиями описывались в релизах. Было трудновато каждый раз вспоминать/пробегать коммиты,
чтобы написать очередное описание к новой версии. С целью удобного ведения изменений проекта был создан
CHANGELOG-файл. В качестве стандарта был выбран [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).
На сайте подробно указано, какие именно изменения должны попадать в CHANGELOG, как эти изменения группировать,
как обновлять файл во время новых релизов - очень доходчиво для новичков, как я.

### Первые github-actions для тестов

И последнее изменение. В проекте уже было тестирование, но проводилось оно мною вручную.
Оставалось только перенести это в github-actions. Когда речь зашла о github-actions,
я сразу всполнил о [@tiangolo](https://github.com/tiangolo). Каждый его проект служит
образцом правильного ведения репозитория. В том числе, и образцом правильных github-actions.
Я сразу пошёл смотреть, как сделано автоматическое тестирование в [fastapi](https://github.com/tiangolo/fastapi).
При попытке создать github-action возникли проблемы с [codecov](https://about.codecov.io).
Казалось, что подключение займёт больше, чем эти две строки:

~~~yml
- name: Upload coverage
  uses: codecov/codecov-action@v3
~~~

Но нет, всё оказалось настолько просто. С частью обычного тестирования проблем не возникло.

Новый github-action заработал с первого раза, что немного удивило меня. После успешного
запуска автоматического тестирования я добавил новые значки в README - для статуса прохождения
тестов и для покрытия кода.
