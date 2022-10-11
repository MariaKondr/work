---
# Front matter
title: "Отчёт по лабораторной работе №6"
subtitle: "Мандатное разграничение прав в Linux"
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

Развить навыки администрирования ОС Linux. Получить первое практическое знакомство с технологией SELinux1.

Проверить работу SELinx на практике совместно с веб-сервером Apache.

# Теоретические сведения

SELinux (англ. Security-Enhanced Linux — Linux с улучшенной безопасностью) — реализация системы принудительного контроля доступа, которая может работать параллельно с классической избирательной системой контроля доступа.[2]

# Выполнение лабораторной работы. Создание программы

1. Подготовка лабораторного стенда (@fig:001) - 

![Подготовка лабораторного стенда](screen\1.png){ #fig:001 width=100%}

![Подготовка лабораторного стенда](screen\2.png){ #fig:002 width=100%}

![Подготовка лабораторного стенда](screen\3.png){ #fig:003 width=100%}

![Подготовка лабораторного стенда](screen\4.png){ #fig:004 width=100%}

![Подготовка лабораторного стенда](screen\5.png){ #fig:005 width=100%}

![Подготовка лабораторного стенда](screen\6.png){ #fig:006 width=100%}

2. Вошла в систему с полученными учётными данными и убедилась, что SELinux работает в режиме enforcing политики targeted с помощью команд getenforce и sestatus(@fig:007)

![getenforce и sestatus](screen\7.png){ #fig:007 width=100%}

3. Обратилась с помощью браузера к веб-серверу, запущенному на вашем компьютере, и убедилась, что последний работает: (@fig:008)

![Обратилась с помощью браузера к веб-серверу, запущенному на компьютере](screen\8.png){ #fig:008 width=100%}

4. Нашла веб-сервер Apache в списке процессов, определила его контекст безопасности и занесла эту информацию в отчёт (httpd_t). (@fig:009)

![Веб-сервер Apache в списке процессов, его контекст безопасности](screen\9.png){ #fig:009 width=100%}

5. Посмотрела текущее состояние переключателей SELinux для Apache. (@fig:010)

![Текущее состояние переключателей SELinux для Apache](screen\10.png){ #fig:010 width=100%}

6. Посмотрела статистику по политике с помощью команды seinfo, также определите множество пользователей, ролей, типов. (@fig:011)

![Cтатистика по политике с помощью команды seinfo](screen\11.png){ #fig:011 width=100%}

- Множество пользователей: 8
- Роли: 14
- Типы: 5002

7. Определила тип файлов и поддиректорий, находящихся в директории /var/www и /var/www/html (@fig:012)

![Тип файлов и поддиректорий, находящихся в директории /var/www и /var/www/html](screen\12.png){ #fig:012 width=100%}

Круг пользователей, которым разрешено создание файлов в
директории - пользователь (user)

8. Создайте от имени суперпользователя (так как в дистрибутиве после установки только ему разрешена запись в директорию) html-файл /var/www/html/test.html (@fig:013) - (@fig:014)

![Создайте от имени суперпользователя html-файл /var/www/html/test.html](screen\13.png){ #fig:013 width=100%}

![Создайте от имени суперпользователя html-файл /var/www/html/test.html (консоль)](screen\14.png){ #fig:014 width=100%}

9. Проверила контекст созданного файла. Занесла в отчёт контекст -  httpd_sys_content_t, присваиваемый по умолчанию вновь созданным файлам в директории /var/www/html (@fig:015)

![Контекст созданного файла](screen\15.png){ #fig:015 width=100%}

10. Обратилась к файлу через веб-сервер, введя в браузере адрес http://127.0.0.1/test.html. Убедилась, что файл был успешно отображён.(@fig:016)

![Обратилась к файлу через веб-сервер, введя в браузере адрес http://127.0.0.1/test.html](screen\16.png){ #fig:016 width=100%}

11. Тип файла test.html - httpd_sys_content_t. Тип httpd_sys_content_t позволяет процессу httpd получить доступ к файлу. Благодаря наличию последнего типа мы получили доступ к файлу при обращении к нему через браузер.(@fig:017)

![Тип файла test.html](screen\17.png){ #fig:017 width=100%}

12. Изменила контекст файла /var/www/html/test.html с
httpd_sys_content_t на samba_share_t(@fig:018)

![Изменила контекст файла test.html с httpd_sys_content_t на samba_share_t](screen\18.png){ #fig:018 width=100%}

13. Попробовала ещё раз получить доступ к файлу через веб-сервер, введя в браузере адрес http://127.0.0.1/test.html.(@fig:019)

![Попробовала ещё раз получить доступ к файлу через веб-сервер](screen\19.png){ #fig:019 width=100%}

14. Просмотрела log-файлы веб-сервера Apache. Также просмотрела системный лог-файл(@fig:020)

![Просмотрела log-файлы веб-сервера Apache. Также просмотрела системный лог-файл](screen\20.png){ #fig:020 width=100%}

15. Попробовала запустить веб-сервер Apache на прослушивание ТСР-порта 81 (а не 80, как рекомендует IANA и прописано в /etc/services). Для этого в файле /etc/httpd/httpd.conf нашла строчку Listen 80 и заменила её на Listen 81. (@fig:021)

![В файле /etc/httpd/httpd.conf нашла строчку Listen 80 и заменила её на Listen 81](screen\21.png){ #fig:021 width=100%}

16. Выполнила перезапуск веб-сервера Apache. Сбой не произошёл. Проанализирова лог-файлы  tail -nl /var/log/messages.(@fig:022)

Просмотрела файлы /var/log/http/error_log, /var/log/http/access_log и /var/log/audit/audit.log и выяснила, в каких файлах появились записи - только в /var/log/audit/audit.log. (@fig:023)

![Проанализирова лог-файлы /var/log/messages](screen\22.png){ #fig:022 width=100%}

![Просмотрела файлы /var/log/http/error_log, /var/log/http/access_log и /var/log/audit/audit.log](screen\23.png){ #fig:023 width=100%}

17.  Выполнила команду semanage port -a -t http_port_t -р tcp 81. После этого проверила список портов командой
semanage port -l | grep http_port_t. Убедилась, что порт 81 появился в списке.(@fig:024)

![Список портов](screen\24.png){ #fig:024 width=100%}

18. Попробовала запустить веб-сервер Apache ещё раз, он снова запустился. Вернула контекст httpd_sys_cоntent__t к файлу /var/www/html/test.html. После этого попробовала получить доступ к файлу через веб-сервер, введя в браузере адрес http://127.0.0.1:81/test.html. (@fig:025)-(@fig:026)

![Запуск веб-сервера Apache ещё раз и возвращение контекста httpd_sys_cоntent__t к файлу test.html](screen\25.png){ #fig:025 width=100%}

![Попытка получить доступ к файлу через веб-сервер, введя в браузере адрес http://127.0.0.1:81/test.html](screen\26.png){ #fig:026 width=100%}

19. Исправила обратно конфигурационный файл apache, вернув Listen 80. (@fig:027)

![Исправила обратно конфигурационный файл apache, вернув Listen 80](screen\27.png){ #fig:027 width=100%}

20. Попыталась удалить привязку http_port_t к 81 порту, что не получилось так как 81 порт defined in policy и не может быть удален. Удалила файл /var/www/html/test.html (@fig:028)

![Попытка удалить привязку http_port_t к 81 порту и удаление файла test.html](screen\28.png){ #fig:028 width=100%}

# Выводы

Выполнила лабораторную работу №6.

Развила навыки администрирования ОС Linux. Получила первое практическое знакомство с технологией SELinux1.

Проверила работу SELinx на практике совместно с веб-сервером Apache.

# Список литературы

1. Методические материалы курса. "Информационная безопасность компьютерных сетей" Кулябов Д. С., Королькова А. В., Геворкян М. Н.
2. https://ru.wikipedia.org/wiki/SELinux