# Leningrad2-DivMMC

DivMMC controller for ZX Spectrum computers.

&#x20; 

\## Описание



&#x20;   Интерфейс DivMMC для легендарного клона Leningrad-2. Позволяет использовать современные SD-карты в качестве накопителя. Работает под управлением операционной системы ESXDOS, обеспечивая мгновенную загрузку игр (TAP, TRD, Z80, SNA) и поддержку длинных имен файлов.

&#x20; 

&#x20;   Проект основан на проверенной схемотехнике от \[AlexEkb](https://github.com/AlexEkb4ever) и реализован на доступной мелкой логике.



\## Историческая справка и контекст



&#x20;   Если BDI (TR-DOS) — это классика 90-х, то DivMMC — это стандарт сегодняшнего дня. Данный контроллер адаптирован специально для моих версий плат \[Leningrad-2-48k](https://github.com/Alex-2-Graf/LENINGRAD-2-48k) и \[Leningrad-2-128k-SRAM](https://github.com/Alex-2-Graf/Leningrad-2-128k-SRAM), где системная шина уже подготовлена. Однако его можно подключить и к любому другому «Ленинграду-2» при минимальных доработках шины.



\## Технические особенности

&#x20; 

Основные возможности



&#x20;  \* Носитель: Поддержка двух SD-карт (MicroSD + разъем для подключения второго модуля).

&#x20;  \* Логика: Собрано на дискретной логике (без использования ПЛИС/CPLD), что упрощает сборку и отладку.

&#x20;  \* Управление: На плате установлены кнопки NMI (вызов меню навигатора ESXDOS) и RESET.

&#x20;  \* ОС: Полная совместимость с ESXDOS (версии 0.8.9 и выше)(загрузка файлов .TAP, .TRD, .SCL, .Z80).

&#x20; 

\[iBOM](https://github.com/Alex-2-Graf/Leningrad2-DivMMC/blob/main/Schematics/DivMMC\_L2.html) \[Схема](https://github.com/Alex-2-Graf/Leningrad2-DivMMC/blob/main/Schematics/DivMMC\_L2.pdf) \[Gerber](https://github.com/Alex-2-Graf/Leningrad2-DivMMC/blob/main/Gerber/DivMMC\_L2\_Gerber.zip)

&#x20; 

!\[](https://github.com/Alex-2-Graf/Leningrad2-DivMMC/blob/main/Photos/1.png)

&#x20; 

!\[](https://github.com/Alex-2-Graf/Leningrad2-DivMMC/blob/main/Photos/2.png)

&#x20; 

!\[](https://github.com/Alex-2-Graf/Leningrad2-DivMMC/blob/main/Photos/DivMMC-L2.jpg)

&#x20; 

\## Подключение



&#x20;   Контроллер подключается к системному разъему. Все необходимые сигналы управления (MREQ, IORQ, M1, RD, WR) и шина данных/адреса задействованы согласно спецификации DivMMC.

&#x20;   Важно: Для корректной работы требуется наличие сигнала M1. На моих версиях плат он выведен штатно.



\## Программное обеспечение и ROM

&#x20; 

Для работы контроллера требуется прошитая микросхема ПЗУ с операционной системой esxDOS.



&#x20;   Важно: В данном проекте используется модифицированная версия прошивки, адаптированная под схемотехнику AlexEkb и особенности шины «Ленинград-2». Необходимый файл прошивки находится в папке /Firmware. \[тут](https://github.com/Alex-2-Graf/Leningrad2-DivMMC/blob/main/Firmware/ROM.bin)

&#x20; 

&#x20;   Официальный сайт проекта esxDOS: esxdos.org (для ознакомления с командами и структурой системных папок на SD-карте).

&#x20;

&#x20;   Карту SD отформатировать в FAT32 и распаковать на неё \[архив](https://github.com/Alex-2-Graf/Leningrad2-DivMMC/blob/main/Firmware/esxdos\_disk.zip)

