---
# Front matter
title: "Отчёт по лабораторной работе №5"
subtitle: "Дискреционное разграничение прав в Linux. Исследование влияния дополнительных атрибутов"
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

Изучение механизмов изменения идентификаторов, применения SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.

# Теоретические сведения

Setuid, Setgid и Sticky Bit - это специальные типы разрешений позволяют задавать расширенные права доступа на файлы или каталоги.

Setuid – это бит разрешения, который позволяет пользователю запускать исполняемый файл с правами владельца этого файла. Другими словами, использование этого бита позволяет нам поднять привилегии пользователя в случае, если это необходимо.

Принцип работы Setgid похож на setuid с отличием, что файл будет запускаться пользователем от имени группы, которая владеет файлом.

В случае, если Sticky Bit установлен для папки, то файлы в этой папке могут быть удалены только их владельцем, тоже самое верно и для файлов.[2]

# Выполнение лабораторной работы. Создание программы

1. Подготовка лабораторного стенда (@fig:001)

![Подготовка лабораторного стенда](screen\1.png){ #fig:001 width=100%}

2. Вошла в систему от имени пользователя guest, создала программу simpleid.c(@fig:002). Скомплилировала программу и выполнила ее, также выполнила системную программу id т сравнила вывод двух программ - вывелись одинаковые значения.(@fig:003)

![Программа simpleid.c](screen\2.png){ #fig:002 width=100%}

![Пункт 1-5](screen\3.png){ #fig:003 width=100%}

3. Усложнила программу, добавив вывод действительных идентификаторов типа (@fig:004), скомпилировала и запустила (@fig:005)

![Программа simpleid2.c](screen\4.png){ #fig:004 width=100%}

![Компилирование и запуск simpleid2.c](screen\5.png){ #fig:005 width=100%}

4. От имени суперпользователя выполнила команды: chown root:guest /home/guest/simpleid2, chmod u+s /home/guest/simpleid2. Также выполнила проверку правильности установки новых атрибутов и смены владельца файла simpleid2: ls -l simpleid2, запустила simpleid2 и id,
результаты которых оказались одинаковыми.(@fig:006)

![SetUID-бит](screen\6.png){ #fig:006 width=100%}

5. Проделала тоже самое относительно SetGID-бита.(@fig:007)

![SetGID-бит](screen\7.png){ #fig:007 width=100%}

6. Создала программу readfile.c (@fig:008)(@fig:009)

![Создание файла readfile.c](screen\8.png){ #fig:008 width=100%}

![Программа readfile.c](screen\9.png){ #fig:009 width=100%}

7. Сменила владельца у файла readfile.c и изменила права так, чтобы только суперпользователь (root) мог прочитать его, a guest не мог.(@fig:010)
  
![Смена прав так, чтобы только суперпользователь мог прочесть файл](screen\10.png){ #fig:010 width=100%}

8. Проверила, что пользователь guest не может прочитать файл readfile.c (@fig:011)
  
![Проверка](screen\11.png){ #fig:011 width=100%}

9. Сменила у программы readfile владельца и установила SetUID-бит. (@fig:012)
  
![readfile SetUID-бит](screen\12.png){ #fig:012 width=100%}

10. Проверила, может ли программа readfile прочитать файл readfile.c - Да, может. (@fig:013)
  
![Проверка чтения файла readfile.c](screen\13.png){ #fig:013 width=100%}

11. Проверила, может ли программа readfile прочитать файл /etc/shadow. - Да, может. (@fig:014)
  
![Проверка чтения файла /etc/shadow](screen\14.png){ #fig:014 width=100%}

# Исследование Sticky-бита

1. Выяснила, установлен ли атрибут Sticky на директории /tmp. От имени пользователя guest создала файл file01.txt в директории /tmp
со словом test. Просмотрела атрибуты у только что созданного файла и разрешила чтение и запись для категории пользователей «все остальные» (@fig:015)

![Атрибут Sticky на директории /tmp и файл file01.txt](screen\15.png){ #fig:015 width=100%}

2. От пользователя guest2 попробовала прочитать файл /tmp/file01.txt, дозаписать в файл, записать в файл слово test3, стерев при этом всю имеющуюся в файле информацию, удалить файл.(@fig:016)

Все удалось кроме удаления файла.

![guest2 и file01](screen\16.png){ #fig:016 width=100%}

3. Повысила свои права до суперпользователя и выполнила после этого команду, снимающую атрибут t (Sticky-бит) с директории /tmp, покинула режим суперпользователя.(@fig:017)

![Снятие атрибута t (Sticky-бит) с директории /tmp](screen\17.png){ #fig:017 width=100%}

4. От пользователя guest2 проверила, что атрибута t у директории /tmp нет, повторила предыдущие шаги.(@fig:018)

Удалось удалить файл от имени пользователя, не являющегося
его владельцем

![Взаимодействие guest2 с файлом, когда атрибута t (Sticky-бит) снят с директории /tmp](screen\18.png){ #fig:018 width=100%}

5. Повысила свои права до суперпользователя и вернула атрибут t на директорию /tmp.(@fig:019)

![Возвращение атрибута t (Sticky-бит) на директорию /tmp](screen\19.png){ #fig:019 width=100%}

# Выводы

Выполнила лабораторную работу №5.

Изучила механизмы изменения идентификаторов, применения SetUID- и Sticky-битов. Получила практические навыки работы в консоли с дополнительными атрибутами. Рассмотрела работы механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.

# Список литературы

1. Методические материалы курса. "Информационная безопасность компьютерных сетей" Кулябов Д. С., Королькова А. В., Геворкян М. Н.
2. https://ruvds.com/ru/helpcenter suid-sgid-sticky-bit-linux/
