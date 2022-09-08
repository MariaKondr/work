---
# Front matter
title: "Отчёт по лабораторной работе №1"
subtitle: "Установка и конфигурация операционной системы на виртуальную машину"
author: "Кондрашина Мария Сергеевна"

# Generic otions
lang: ru-RU
toc-title: "Содержание"

# Pdf output format
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
### Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
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
## Misc options
indent: true
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Целью данной работы является приобретение практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

# Выполнение лабораторной работы

1. Окно «Имя машины и тип ОС»

![Окно «Имя машины и тип ОС»](1.png){ #fig:001 width=100%}

2.  Окно «Размер основной памяти»

![Окно «Размер основной памяти»](2.png){ #fig:002 width=100%}

3. Окно подключения или создания жёсткого диска на виртуальной машине

![Окно подключения или создания жёсткого диска на виртуальной машине](3.png){ #fig:003 width=100%}

4.  Окно определения типа подключения виртуального жёсткого диска

![ Окно определения типа подключения виртуального жёсткого диска](4.png){ #fig:004 width=100%}

5. Окно определения формата виртуального жёсткого диска

![Окно определения формата виртуального жёсткого диска](5.png){ #fig:005 width=100%}

6. Окно определения размера виртуального динамического жёсткого
диска и его расположения

![Окно определения размера виртуального динамического жёсткого диска и его расположения](6.png){ #fig:006 width=100%}

7.  Окно «Носители» виртуальной машины: подключение образа оптического диска

![ Окно «Носители» виртуальной машины: подключение образа оптического диска](7.png){ #fig:007 width=100%}

8. Носители виртуальной машины

![Носители виртуальной машины](8.png){ #fig:008 width=100%}

9. Запуск виртуальной машины

![ Запуск виртуальной машины](9.png){ #fig:009 width=100%}

10. Установка английского языка интерфейса ОС

![Установка английского языка интерфейса ОС](10.png){ #fig:010 width=100%}

11. Добавление русского языка, но в качестве языка по умолчанию
указан английский язык; задана комбинация клавиш для переключения
между раскладками клавиатуры (Alt_Shift)

![Добавление русского языка, но в качестве языка по умолчанию указан английский язык](11.png){ #fig:011 width=100%}

12. Окно настройки установки: выбор программ

![Окно настройки установки: выбор программ](12.png){ #fig:012 width=100%}

13. Окно настройки установки: место установки

![Окно настройки установки: место установки](13.png){ #fig:013 width=100%}

14. Окно настройки установки: сеть и имя узла

![Окно настройки установки: сеть и имя узла](14.png){ #fig:014 width=100%}

15. Установка пароля для root

![Установка пароля для root](15.png){ #fig:015 width=100%}

16. Установка пароля для пользователя с правами администратора

![ Установка пароля для пользователя с правами администратора](16.png){ #fig:016 width=100%}

17. Завершение установки ОС

![ Завершение установки ОС](17.png){ #fig:017 width=100%}

# Домашнее задание

1. Выполнение команды dmesg

![Вывод команды dmesg](19.png){ #fig:018 width=100%}

2. Выполнение команды dmesg | less

![Вывод команды dmesg | less](21.png){ #fig:019 width=100%}

![Вывод команды dmesg | less](20.png){ #fig:020 width=100%}

Получение следующей информации:

1. Версия ядра Linux (Linux version).

![Версия ядра Linux (Linux version)](22.png){ #fig:021 width=100%}

2. Частота процессора (Detected Mhz processor). Частота 1992.003 MHz.

![Частота процессора (Detected Mhz processor)](23.png){ #fig:022 width=100%}

3. Модель процессора (CPU0).

![Модель процессора (CPU0)](24.png){ #fig:023 width=100%}

4. Объем доступной оперативной памяти (Memory available). 260860/2096696K доступно.

![Объем доступной оперативной памяти (Memory available)](25.png){ #fig:024 width=100%}

5. Тип обнаруженного гипервизора (Hypervisor detected). Тип - KVM.

![Тип обнаруженного гипервизора (Hypervisor detected)](26.png){ #fig:025 width=100%}

6. Тип файловой системы корневого раздела. Вывожу все файловые системы при помощи команды df -Th. Тип файловой системы корневого раздела - xfs.

![Тип файловой системы корневого раздела](27.png){ #fig:026 width=100%}

1. Последовательность монтирования файловых систем. Для вывода использовала команду findmnt.

![Последовательность монтирования файловых систем](30.png){ #fig:027 width=100%}

# Выводы

Выполнила лабораторную работу №1. Приобрела практические навыки
установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

# Список литературы

1. Методические материалы курса. "Информационная безопасность компьютерных сетей" Кулябов Д. С., Королькова А. В., Геворкян М. Н.