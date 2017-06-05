# Проект "Рендзю"

Баранов Юрий, группа 153

### Постановка задачи

В последнее время стало принято измерять прогресс в разработке искусственного интеллекта на сложных логических задачах, таких как игры с полной информацией. В качестве такой игры, подходят, например, шахматы. Впервые партия в шахматы человека против компьютера состоялась в 1996 году. До недавнего времени одной из игр, для которых не удавалось придумать стратегию, обыгрывающую профессиональных игроков, была игра Го. В 2015 году группа DeepMind разработала глубокую нейронную сеть [AlphaGo](https://en.wikipedia.org/wiki/AlphaGo), которой удалось это сделать. Данная нейронная сеть и методы, применявшиеся для ее обучения взяты за основу проекта. Задача состоит в создании и обучении аналогичной нейронной сети для игры Ренздю.


### Цели:

1. Освоить в теории и научиться реализовывать различные виды нейронных сетей.

2. Придумать и реализовать стратегию игры в Рендзю.

3. Улучшить навыки программирования на Python.

4. Изучить популярные библиотеки и инструменты для анализа данных и вычислений.


### Архитектура и методы обучения

1. Будут изучены и реализованы сверточные нейронные сети.

2. По аналогии с AlphaGo будут использованы несколько нейронных сетей: для оценки вероятности выигрыша, вероятности того, что конкретный ход сделал бы профессиональный игрок.

3. Сначала программа будет обучаться на партиях профессиональных игроков, затем дообучаться, играя со своими предыдущими версиями.


### Технологические решения

1. Основной язык - Python3. Выбор обусловлен простотой и наличием необходимых для машинного обучения библиотек.

2. Для написания лабораторных работ и отчетов будут использованы Jupyter notebook и библиотека для работы с графиками matplotlib.

3. Для написания и обучения нейронных сетей планируется использовань keras и thenano.

### План реализации

Октябрь - Декабрь: Лабораторные работы по применению основных методов, которые планируется использовать.

После завершения лабораторных работ, планируется начать реализацию проекта. С февраля по март должен появиться законченный прототип, играющий на среднем уровне.

Январь - Март: Сбор данных, реализация нейронной сети и обучение.

Март - Апрель: Реализация дерева поиска Монте Карло.

Апрель - Май: Дообучение и итоговое соревнование.


# Отчет

### Описание алгоритма

Написана и обучена сверточная нейронная сеть, предсказывающая по состоянию доски следующий ход игрока. Краткое описание архитектуры: 3 сверточных и полносвязных слоя.

Выбор хода происходит с помощью дерева поиска Монте Карло. На каждом уровне берутся 5 лучших ходов по предсказанию нейросети. Для выбора хода на первых 4 уровнях симуляции используется upper-confidence-bound-algorithm. На последующих уровнях выбирается наилучший по предсказанию нейросети ход. После каждой завершенной симуляции обновляются ожидаемые вероятности выигрыша для каждого выбранного хода. После завершени симуляций выбирается ход с максимальной вероятностью выигрыша. В целях оптимизации добавлены две эвристики: проверка возможности выигрыша за 1 и 2 хода, в случае наличия которых, текущая симуляция завершается.

### Результаты соревнования среди 5 участников проекта (10 секунд на ход)

За черных (начинают игру): 3 победы, 1 поражение.
За белых: 2 ничьи, 2 поражения.


