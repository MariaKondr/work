---
# Front matter
title: "Отчёт по лабораторной работе №4"
subtitle: "Дискреционное разграничение прав в Linux. Расширенные атрибуты"
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

Получение практических навыков работы в консоли с расширенными атрибутами файлов.

# Теоретические сведения

Файловые атрибуты могут использовать администраторы и пользователи для защиты файлов от случайных удалений и изменений, а также их применяют злоумышленники, делая невозможным удаление вредоносного файла.

Файл с установленным атрибутом «a» можно открыть только в режиме добавления для записи.

Файл с атрибутом «i» не может быть изменён: его нельзя удалить или переименовать, нельзя создать ссылку на этот файл, большую часть метаданных файла нельзя изменить, и файл нельзя открыть в режиме записи. [2]

# Выполнение лабораторной работы

1. От имени пользователя guest определила расширенные атрибуты файла /home/guest/dir1/file1 командой, установила командой chmod 600 file1 на файл file1 права, разрешающие чтение и запись для владельца файла, попробовала установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest, на что получила отказ.(@fig:001)

![пункты 1-3](screen\1.png){ #fig:001 width=100%}

2. Зашла на вторую консоль с правами администратора (su root). Установила расширенный атрибут a на файл /home/guest/dir1/file1 от имени суперпользователя, от пользователя guest проверила правильность установления атрибута, попробовала стереть имеющуюся в нём информацию, выполнила дозапись в файл file1 слова «test», после этого выполнила чтение файла file1, попробовала удалить файл file1, переименовать файл, а также изменить права у файла.(@fig:002)

![С расширенным атрибутом а](screen\5.png){ #fig:002 width=100%}

3. Сняла расширенный атрибут a с файла /home/guest/dirl/file1 от имени суперпользователя командой chattr -a /home/guest/dir1/file1 и повторила операции, которые ранее не удавалось выполнить(@fig:003)

![Без расширенных атрибутов](screen\6.png){ #fig:003 width=100%}

4. Повторила действия по шагам, заменив атрибут «a» атрибутом «i». В данном случае дозаписать файл не удалось. (@fig:004)

![С расширенным атрибутом i](screen\7.png){ #fig:004 width=100%}

5. Таблица, показыващая возможные действия при различных расширенных атрибутах. (@fig:005)

![Таблица, возможных действий при различных расширенных атрибутах](screen\8.png){ #fig:005 width=100%}

# Выводы

Выполнила лабораторную работу №4.
В результате выполнения работы повысила свои навыки использования интерфейса командой строки, познакомилась на примерах с тем, как используются основные и расширенные атрибуты при разграничении доступа.

# Список литературы

1. Методические материалы курса. "Информационная безопасность компьютерных сетей" Кулябов Д. С., Королькова А. В., Геворкян М. Н.
2. https://zalinux.ru/?p=6440