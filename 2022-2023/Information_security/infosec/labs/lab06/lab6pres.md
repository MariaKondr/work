---
## Front matter
lang: ru-RU
title: Лабораторная работа №6
author: |
	Кондрашина Мария Сергеевна\inst{1}
institute: |
	\inst{1}RUDN University, Moscow, Russian Federation
date: 11.10.2022, Moscow

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

# Мандатное разграничение прав в Linux

## Цель работы

Развитие навыков администрирования ОС Linux. Получение первого практического знакомства с технологией SELinux1.

Проверка работы SELinx на практике совместно с веб-сервером Apache.

# Теоретические сведения

SELinux (англ. Security-Enhanced Linux — Linux с улучшенной безопасностью) — реализация системы принудительного контроля доступа, которая может работать параллельно с классической избирательной системой контроля доступа.

# Выполнение лабораторной работы

## Подготовка лабораторного стенда

![](screen\1.png){ #fig:001 width=100%}

## Подготовка лабораторного стенда

![](screen\2.png){ #fig:002 width=100%}

## Подготовка лабораторного стенда

![](screen\3.png){ #fig:003 width=100%}

## Подготовка лабораторного стенда

![](screen\4.png){ #fig:004 width=100%}

## Подготовка лабораторного стенда

![](screen\5.png){ #fig:005 width=100%}

## Подготовка лабораторного стенда

![](screen\6.png){ #fig:006 width=100%}

## Вошла в систему с полученными учётными данными и убедилась, что SELinux работает в режиме enforcing политики targeted с помощью команд getenforce и sestatus

![](screen\7.png){ #fig:007 width=100%}

## Обратилась с помощью браузера к веб-серверу, запущенному на компьютере

![](screen\8.png){ #fig:008 width=100%}

## Веб-сервер Apache в списке процессов, его контекст безопасности

![](screen\9.png){ #fig:009 width=100%}

## Текущее состояние переключателей SELinux для Apache

![](screen\10.png){ #fig:010 width=100%}

## Cтатистика по политике с помощью команды seinfo

![](screen\11.png){ #fig:011 width=100%}

## Тип файлов и поддиректорий, находящихся в директории /var/www и /var/www/html

![](screen\12.png){ #fig:012 width=100%}

## Создание от имени суперпользователя html-файл /var/www/html/test.html

![](screen\14.png){ #fig:014 width=100%}

## Контекст созданного файла

![](screen\15.png){ #fig:015 width=100%}

## Обратилась к файлу через веб-сервер, введя в браузере адрес http://127.0.0.1/test.html

![](screen\16.png){ #fig:016 width=100%}

## Тип файла test.html

![](screen\17.png){ #fig:017 width=100%}

## Изменила контекст файла test.html с httpd_sys_content_t на samba_share_t

![](screen\18.png){ #fig:018 width=100%}

## Попробовала ещё раз получить доступ к файлу через веб-сервер

![](screen\19.png){ #fig:019 width=100%}

## Просмотрела log-файлы веб-сервера Apache. Также просмотрела системный лог-файл

![](screen\20.png){ #fig:020 width=100%}

## В файле /etc/httpd/httpd.conf нашла строчку Listen 80 и заменила её на Listen 81

![](screen\21.png){ #fig:021 width=100%}

## Проанализирова лог-файлы /var/log/messages

![](screen\22.png){ #fig:022 width=100%}

## Просмотрела файлы /var/log/http/error_log, /var/log/http/access_log и /var/log/audit/audit.log

![](screen\23.png){ #fig:023 width=100%}

## Список портов

![](screen\24.png){ #fig:024 width=100%}

## Запуск веб-сервера Apache ещё раз и возвращение контекста httpd_sys_cоntent__t к файлу test.html

![](screen\25.png){ #fig:025 width=100%}

## Попытка получить доступ к файлу через веб-сервер, введя в браузере адрес http://127.0.0.1:81/test.html

![](screen\26.png){ #fig:026 width=100%}

## Исправила обратно конфигурационный файл apache, вернув Listen 80

![](screen\27.png){ #fig:027 width=100%}

## Попытка удалить привязку http_port_t к 81 порту и удаление файла test.html

![](screen\28.png){ #fig:028 width=100%}

## Результат

- Выполнила лабораторную работу №6.
- Развила навыки администрирования ОС Linux. Получила первое практическое знакомство с технологией SELinux1.
- Проверила работу SELinx на практике совместно с веб-сервером Apache.

## Список литературы

1. Методические материалы курса. "Информационная безопасность компьютерных сетей" Кулябов Д. С., Королькова А. В., Геворкян М. Н.
2. https://ru.wikipedia.org/wiki/SELinux