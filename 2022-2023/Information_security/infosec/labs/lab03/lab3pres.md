---
## Front matter
lang: ru-RU
title: Лабораторная работа №3
author: |
	Кондрашина Мария Сергеевна\inst{1}
institute: |
	\inst{1}RUDN University, Moscow, Russian Federation
date: 19.09.2022, Moscow

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

# Дискреционное разграничение прав в Linux. Два пользователя

## Цель работы

Получение практических навыков работы в консоли с атрибутами файлов для групп пользователей.

# Выполнение лабораторной работы

## Учетная запись guest2

![](screen\1.png){ #fig:001 width=100%}

## Вход в систему от двух пользователей на двух разных консолях

![](screen\2.png){ #fig:002 width=100%}

## Просмотрела файл командой cat /etc/group

![](screen\3.png){ #fig:003 width=100%}

## 

![](screen\4.png){ #fig:004 width=100%}

## Регистрация пользователя guest2 в группе guest

![](screen\5.png){ #fig:005 width=100%}

## Изменила права директории /home/guest, разрешив все действия для пользователей группы

![](screen\6.png){ #fig:006 width=100%}

## Заполнила таблицу «Установленные права и разрешённые действия для групп»

![d(000)](screen\7.png){ #fig:007 width=100%}

## d(010)

![d(010)](screen\8.png){ #fig:008 width=100%}

## d(020)

![d(020)](screen\9.png){ #fig:009 width=100%}

## d(030)

![d(030)](screen\10.png){ #fig:010 width=100%}

## d(040)

![d(040)](screen\11.png){ #fig:011 width=100%}

## d(050)

![d(050)](screen\12.png){ #fig:012 width=100%}

## d(060)

![d(060)](screen\13.png){ #fig:013 width=100%}

## d(070)

![d(070)](screen\14.png){ #fig:014 width=100%}

## Минимально необходимые права для выполнения операций операций от имени пользователей входящих в группу

![](screen\15.png){ #fig:015 width=100%}

## Результат

- Выполнила лабораторную работу №3.
- Получила практические навыки работы в консоли с атрибутами файлов для групп пользователей.

## Список литературы

1. Методические материалы курса. "Информационная безопасность компьютерных сетей" Кулябов Д. С., Королькова А. В., Геворкян М. Н.