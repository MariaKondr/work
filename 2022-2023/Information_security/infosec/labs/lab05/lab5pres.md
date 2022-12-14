---
## Front matter
lang: ru-RU
title: Лабораторная работа №5
author: |
	Кондрашина Мария Сергеевна\inst{1}
institute: |
	\inst{1}RUDN University, Moscow, Russian Federation
date: 05.10.2022, Moscow

## Formatting
toc: false
slide_level: 2
theme: metropolis
header-includes: 
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
aspectratio: 43
section-titles: true
---  

# Дискреционное разграничение прав в Linux. Исследование влияния дополнительных атрибутов

## Цель работы

Изучение механизмов изменения идентификаторов, применения SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.

# Теоретические сведения

Setuid, Setgid и Sticky Bit - это специальные типы разрешений позволяют задавать расширенные права доступа на файлы или каталоги.

## Setuid

Setuid – это бит разрешения, который позволяет пользователю запускать исполняемый файл с правами владельца этого файла. Другими словами, использование этого бита позволяет нам поднять привилегии пользователя в случае, если это необходимо.

## Setgid

Принцип работы Setgid похож на setuid с отличием, что файл будет запускаться пользователем от имени группы, которая владеет файлом.

## Sticky Bit

В случае, если Sticky Bit установлен для папки, то файлы в этой папке могут быть удалены только их владельцем, тоже самое верно и для файлов.

# Выполнение лабораторной работы

# Создание программы 

## Подготовка лабораторного стенда

![](screen\1.png){ #fig:001 width=100%}

## Вошла в систему от имени пользователя guest, создала программу simpleid.c

![](screen\2.png){ #fig:002 width=100%}

## Скомплилировала программу и выполнила ее, также выполнила системную программу id т сравнила вывод двух программ - вывелись одинаковые значения

![](screen\3.png){ #fig:003 width=100%}

## Программа simpleid2.c (вывод действительных идентификаторов )

![](screen\4.png){ #fig:004 width=100%}

## Компилирование и запуск simpleid2.c

![](screen\5.png){ #fig:005 width=100%}

## От имени суперпользователя выполнила команды: chown root:guest /home/guest/simpleid2, chmod u+s /home/guest/simpleid2

![](screen\6.png){ #fig:006 width=100%}

## SetGID-бита

![](screen\7.png){ #fig:007 width=100%}

## Создание файла readfile.c

![](screen\9.png){ #fig:009 width=100%}

## Смена прав так, чтобы только суперпользователь мог прочесть файл

![](screen\10.png){ #fig:010 width=100%}

## Проверка

![](screen\11.png){ #fig:011 width=100%}

## Сменила у программы readfile владельца и установила SetUID-бит

![](screen\12.png){ #fig:012 width=100%}

## Проверка чтения файла readfile.c

![](screen\13.png){ #fig:013 width=100%}

## [Проверка чтения файла /etc/shadow

![](screen\14.png){ #fig:014 width=100%}

# Исследование Sticky-бита

## Атрибут Sticky на директории /tmp и файл file01.txt

![](screen\15.png){ #fig:015 width=100%}

## guest2 и file01

![](screen\16.png){ #fig:016 width=100%}

## Снятие атрибута t (Sticky-бит) с директории /tmp

![](screen\17.png){ #fig:017 width=100%}

## Взаимодействие guest2 с файлом, когда атрибута t (Sticky-бит) снят с директории /tmp

![](screen\18.png){ #fig:018 width=100%}

## Возвращение атрибута t (Sticky-бит) на директорию /tmp

![](screen\19.png){ #fig:019 width=100%}


## Результат

- Выполнила лабораторную работу №5.
- Изучила механизмы изменения идентификаторов, применения SetUID- и Sticky-битов.
- Получила практические навыки работы в консоли с дополнительными атрибутами.
- Рассмотрела работы механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.

## Список литературы

1. Методические материалы курса. "Информационная безопасность компьютерных сетей" Кулябов Д. С., Королькова А. В., Геворкян М. Н.
2. https://ruvds.com/ru/helpcenter suid-sgid-sticky-bit-linux/