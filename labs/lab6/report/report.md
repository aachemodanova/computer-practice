---
## Front matter
title: "Лабораторная работа №6"
subtitle: "Решение моделей в непрерывном и дискретном времени"
author: "Чемоданова Ангелина Александровна"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: false # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Введение

## Цели и задачи

**Цель работы**

Основной целью работы является освоение специализированных пакетов для решения задач в непрерывном и дискретном времени[@julialang].

**Задание**

1. Используя Jupyter Lab, повторите примеры.

2. Выполните задания для самостоятельной работы[@juliadoc].

# Выполнение лабораторной работы

## Решение обыкновенных дифференциальных уравнений

Вспомним, что обыкновенное дифференциальное уравнение (ОДУ) описывает изменение некоторой переменной u.

Для решения обыкновенных дифференциальных уравнений (ОДУ) в Julia можно использовать пакет diffrentialEquations.jl.

## Модель экспоненциального роста

Рассмотрим пример использования этого пакета для решение уравнения модели экспоненциального роста, описываемую уравнением, где a — коэффициент роста. 

Численное решение в Julia будет иметь следующий вид, а также график, 
соответствующий полученному решению (рис. [-@fig:001] - рис. [-@fig:002]):

![График модели экспоненциального роста](image/1.png){ #fig:001 width=100% height=100% }

![График модели экспоненциального роста](image/2.png){ #fig:002 width=100% height=100% }

При построении одного из графиков использовался вызов sol.t, чтобы захватить массив моментов времени. Массив решений можно получить, воспользовавшись sol.u.

Если требуется задать точность решения, то можно воспользоваться параметрами abstol (задаёт близость к нулю) и reltol (задаёт относительную точность). По умолчанию эти параметры 
имеют значение abstol = 1e-6 и reltol = 1e-3.

Для модели экспоненциального роста (рис. [-@fig:003]):

![График модели экспоненциального роста (задана точность решения)](image/3.png){ #fig:003 width=100% height=100% }

## Система Лоренца

Динамической системой Лоренца является нелинейная автономная система обыкновенных дифференциальных уравнений третьего порядка.

Система получена из системы уравнений Навье–Стокса и описывает движение воздушных потоков в плоском слое жидкости постоянной толщины при разложении скорости течения и температуры в двойные ряды Фурье с последующем усечением до первых-вторых гармоник.

Решение системы неустойчиво на аттракторе, что не позволяет применять классические численные методы на больших отрезках времени, требуется использовать высокоточные вычисления.

Численное решение в Julia будет иметь следующий вид (рис. [-@fig:004]):

![Аттрактор Лоренца](image/4.png){ #fig:004 width=100% height=100% }

Можно отключить интерполяцию (рис. [-@fig:005]):

![Аттрактор Лоренца (интерполяция отключена)](image/5.png){ #fig:005 width=100% height=100% }

## Модель Лотки–Вольтерры

Модель Лотки–Вольтерры описывает взаимодействие двух видов типа «хищник – жертва».

Численное решение в Julia будет иметь следующий вид (рис. [-@fig:006]):

![Модель Лотки–Вольтерры: динамика изменения численности популяций](image/6.png){ #fig:006 width=100% height=100% }

Фазовый портрет (рис. [-@fig:007]):

![Модель Лотки–Вольтерры: фазовый портрет](image/7.png){ #fig:007 width=100% height=100% }

## Самостоятельное выполнение

Выполнение задания №1 (рис. [-@fig:008] - рис. [-@fig:009]):

![Решение задания №1](image/8.png){ #fig:008 width=100% height=100% }

![Решение задания №1](image/9.png){ #fig:009 width=100% height=100% }

Выполнение задания №2 (рис. [-@fig:010] - рис. [-@fig:011]):

![Решение задания №2](image/10.png){ #fig:010 width=100% height=100% }

![Решение задания №2](image/11.png){ #fig:011 width=100% height=100% }

Выполнение задания №3 (рис. [-@fig:012] - рис. [-@fig:014]):

![Решение задания №3](image/12.png){ #fig:012 width=100% height=100% }

![Решение задания №3](image/13.png){ #fig:013 width=100% height=100% }

![Решение задания №3](image/14.png){ #fig:014 width=100% height=100% }

Выполнение задания №4 (рис. [-@fig:015] - рис. [-@fig:016]):

![Решение задания №4](image/15.png){ #fig:015 width=100% height=100% }

![Решение задания №4](image/16.png){ #fig:016 width=100% height=100% }

Выполнение задания №5 (рис. [-@fig:017] - рис. [-@fig:019]):

![Решение задания №5](image/17.png){ #fig:017 width=100% height=100% }

![Решение задания №5](image/18.png){ #fig:018 width=100% height=100% }

![Решение задания №5](image/19.png){ #fig:019 width=100% height=100% }

Выполнение задания №6 (рис. [-@fig:020] - рис. [-@fig:022]):

![Решение задания №6](image/20.png){ #fig:020 width=100% height=100% }

![Решение задания №6](image/21.png){ #fig:021 width=100% height=100% }

![Решение задания №6](image/22.png){ #fig:022 width=100% height=100% }

Выполнение задания №7 (рис. [-@fig:023] - рис. [-@fig:025]):

![Решение задания №7](image/23.png){ #fig:023 width=100% height=100% }

![Решение задания №7](image/24.png){ #fig:024 width=100% height=100% }

![Решение задания №7](image/25.png){ #fig:025 width=100% height=100% }

Выполнение задания №8 (рис. [-@fig:026] - рис. [-@fig:027]):

![Решение задания №8](image/26.png){ #fig:026 width=100% height=100% }

![Решение задания №8](image/27.png){ #fig:027 width=100% height=100% }

# Выводы

В результате выполнения данной лабораторной работы мы освоили специализированные пакеты для решения задач в непрерывном и дискретном времени.

# Список литературы{.unnumbered}

::: {#refs}
:::
