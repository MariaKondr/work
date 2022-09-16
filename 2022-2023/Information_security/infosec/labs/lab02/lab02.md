---
# Front matter
title: "Отчёт по лабораторной работе №2"
subtitle: "Дискреционное разграничение прав в Linux. Основные атрибуты"
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

Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

# Выполнение лабораторной работы

1. В установленной при выполнении предыдущей лабораторной работы операционной системе создала учётную запись пользователя guest. Задала пароль для пользователя guest. (@fig:001)

![Учетная запись guest](screen\1.png){ #fig:001 width=100%}

2. Вошла в систему от имени пользователя guest.(@fig:002)

![Учетная запись guest](screen\2.png){ #fig:002 width=100%}

3. Определилила директорию, в которой нахожусь, командой pwd. Сравнила её с приглашением командной строки. Определила, является ли она
вашей домашней директорией? - Да, она является.(@fig:003)

![Определение директории](screen\3.png){ #fig:003 width=100%}

4. Уточнила имя пользователя командой whoami.(@fig:004)

![Имя пользователя(команда whoami)](screen\4.png){ #fig:004 width=100%}

5. Уточнила имя пользователя, его группу, а также группы, куда входит пользователь, командой id. Выведенные значения uid, gid и др. запомнила. Сравнила вывод id с выводом команды groups(@fig:005)(@fig:006)

![Имя пользователя(команда id)](screen\5.png){ #fig:005 width=100%}

![Имя пользователя(команда groups)](screen\6.png){ #fig:006 width=100%}

Вывод команды id и выводом команды group одинаковы.

6. Просмотрела файл /etc/passwd командой cat /etc/passwd. (@fig:007)(@fig:008)

![Файл /etc/passwd](screen\7.png){ #fig:007 width=100%}

![сat /etc/passwd | grep guest](screen\8.png){ #fig:008 width=100%}

9. Определила существующие в системе директории командой ls -l /home/(@fig:009)

Удалось получить список поддиректорий директории /home.

Какие права установлены на директориях? - Чтение, запись, выполнение

![Существующие в системе директории](screen\9.png){ #fig:009 width=100%}

10. Проверила, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home, командой: lsattr /home. (@fig:010)

Удалось увидеть расширенные атрибуты директории. Не удалось ли увидеть расширенные атрибуты директорий других
пользователей.

![Проверила, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home](screen\10.png){ #fig:010 width=100%}

11. Создала в домашней директории поддиректорию dir1 командой mkdir dir1.(@fig:011)

Определила командами ls -l и lsattr, какие права доступа и расширенные атрибуты были выставлены на директорию dir1 - drwxrwxr-x.(@fig:012)

![Создала в домашней директории поддиректорию dir1](screen\11.png){ #fig:011 width=100%}

![ls -l и lsattr](screen\12.png){ #fig:012 width=100%}

12. Сняла с директории dir1 все атрибуты командой chmod 000 dir1 и проверила правильность выполнения командой ls -l. (@fig:013)

![Сняла с директории dir1 все атрибуты командой chmod 000 dir1 и проверила правильность выполнения командой ls -l](screen\13.png){ #fig:013 width=100%}

13. Попыталась создать в директории dir1 файл file1 командой echo "test" > /home/guest/dir1/file1 (@fig:014)

![Попыталась создать в директории dir1 файл file1](screen\14.png){ #fig:014 width=100%}

Получили отказ в выполнении операции по созданию файла так как нет прав на изменение папки/запись.
Оцените, как сообщение об ошибке отразилось на создании файла? Проверила командой ls -l /home/guest/dir1 действительно ли файл file1 не находится внутри директории dir1. (@fig:015)

![Попыталась создать в директории dir1 файл file1](screen\15.png){ #fig:015 width=100%}

14. Заполнила таблицу «Установленные права и разрешённые действия» (@fig:016) - (@fig:023)

Команды, которые использовались в процессе заполнение таблицы:

touch file1 - создание файла

rm file1 - удаление файла

echo "test" > file1 - запись в файл

cat file1 - чтение файла

cd dir1- смена директории

ls - просмотр файлов в директории

mv -f file1 newfile - переименование файла

chmod _ file1 - смена атрибутов файла

![d(000)](screen\19.png){ #fig:016 width=100%}

![d(100)](screen\20.png){ #fig:017 width=100%}

![d(200)](screen\21.png){ #fig:018 width=100%}

![d(300)](screen\22.png){ #fig:019 width=100%}

![d(400)](screen\23.png){ #fig:020 width=100%}

![d(500)](screen\24.png){ #fig:021 width=100%}

![d(600)](screen\25.png){ #fig:022 width=100%}

![d(700)](screen\26.png){ #fig:023 width=100%}

15. На основании заполненных таблиц определила те или иные минимально необходимые права для выполнения операций внутри директории dir1. (@fig:024)

![Минимально необходимые права для выполнения операций внутри директории dir1](screen\27.png){ #fig:024 width=100%}

# Выводы

Выполнила лабораторную работу №2. Получила практические навыки работы в консоли с атрибутами файлов, закрепления теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

# Список литературы

1. Методические материалы курса. "Информационная безопасность компьютерных сетей" Кулябов Д. С., Королькова А. В., Геворкян М. Н.