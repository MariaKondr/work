---
# Front matter
title: "Отчёт по лабораторной работе №3"
subtitle: "Дискреционное разграничение прав в Linux. Два пользователя"
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

Получение практических навыков работы в консоли с атрибутами файлов для групп пользователей.

# Выполнение лабораторной работы

1. В установленной при выполнении операционной системе создала учётную запись пользователя guest2. Задала пароль для пользователя guest2. Добавила пользователя guest2 в группу guest(@fig:001)

![Учетная запись guest2](screen\1.png){ #fig:001 width=100%}

2. Осуществила вход в систему от двух пользователей на двух разных консолях: guest на первой консоли и guest2 на второй консоли.(@fig:002)

При вводе команды pwd выдалась не домашняя директория для пользователя guest/guest2, а домашняя для mskondrashina.

![Вход в систему от двух пользователей на двух разных консолях](screen\2.png){ #fig:002 width=100%}

3. Сравнила полученную информацию с содержимым файла /etc/group(она совпала). Просмотрела файл командой cat /etc/group(@fig:003)(@fig:004)

![Просмотрела файл командой cat /etc/group](screen\3.png){ #fig:003 width=100%}

![Просмотрела файл командой cat /etc/group 2](screen\4.png){ #fig:004 width=100%}

4. От имени пользователя guest2 выполнила регистрацию пользователя guest2 в группе guest командой: new guest. (@fig:005)

![Регистрация пользователя guest2 в группе guest](screen\5.png){ #fig:005 width=100%}

5.  От имени пользователя guest изменила права директории /home/guest, разрешив все действия для пользователей группы: chmod g+rwx /home/guest.(@fig:006)

![Изменила права директории /home/guest, разрешив все действия для пользователей группы](screen\6.png){ #fig:006 width=100%}

6.  Заполнила таблицу «Установленные права и разрешённые действия для групп» (@fig:007) - (@fig:014)

Команды, которые использовались в процессе заполнение таблицы:

chmod *** dir1 - смена атрибутов директории

chmod *** dir1/file1 - смена атрибутов файла

touch file1 - создание файла

rm file1 - удаление файла

echo "test" > file1 - запись в файл

cat file1 - чтение файла

cd dir1- смена директории

ls - просмотр файлов в директории

mv -f file1 newfile - переименование файла

mkdir dir2 - создание папки dir2 

![d(000)](screen\7.png){ #fig:007 width=100%}

![d(010)](screen\8.png){ #fig:008 width=100%}

![d(020)](screen\9.png){ #fig:009 width=100%}

![d(030)](screen\10.png){ #fig:010 width=100%}

![d(040)](screen\11.png){ #fig:011 width=100%}

![d(050)](screen\12.png){ #fig:012 width=100%}

![d(060)](screen\13.png){ #fig:013 width=100%}

![d(070)](screen\14.png){ #fig:014 width=100%}

1.  На основании заполненных таблиц определила те или иные минимально необходимые права для выполнения операций от имени пользователей входящих в группу. (@fig:015)

![Минимально необходимые права для выполнения операций операций от имени пользователей входящих в группу](screen\15.png){ #fig:015 width=100%}

# Выводы

Выполнила лабораторную работу №2. Получила практические навыки работы в консоли с атрибутами файлов для групп пользователей.

# Список литературы

1. Методические материалы курса. "Информационная безопасность компьютерных сетей" Кулябов Д. С., Королькова А. В., Геворкян М. Н.