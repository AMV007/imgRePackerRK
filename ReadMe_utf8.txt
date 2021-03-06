﻿[ 03.05.2017 ]=====================================================================================

		imgRePackerRK.exe&imgrepackerrk
		version 1.06 (windows&linux)
		(c) RedScorpio, Moscow, 2013-2017

	Программа для распаковки/запаковки образов прошивок RockChip (*.img)

    Назначение:
    Распаковка для внесения изменений и последующей запаковки образов прошивок формата RockChip.
Также можно использовать для исправления контрольных сумм md5 и RockChip CRC. 

    Возможности:
	- распаковка и запаковка RKFW-образов прошивок (с возможностью обработки файлов 2-го слоя)
	  поддерживается старый и новый тип;
	- распаковка и запаковка RKAF-образов прошивок (с возможностью обработки файлов 2-го слоя);
	- распаковка и запаковка файлов 2-го слоя, поддерживаются:
		- Android boot image (04);
		- RockChip bootloader image (15);
		- gzip/cpio archive file (14);
		- cpio_ascii_new archive file (19);
		- Rockchip resources image (30);
		- Rockchip uboot image file (39).
	- проверка и исправление контрольных сумм md5, SHA и RockChip CRC;
	- создание конфигурационных файлов для RKAndroidTool v.1.xx/2.xx.

    Проверено на прошивках:
	- RK???? (ChipID=0x00000021);
	- RK29xx (ChipID=0x00000050);
	- RK30xx (ChipID=0x00000060);
	- RK31xx (ChipID=0x00000070);
	- RK32xx (ChipID=0x00000080);
	- RK33xx (ChipID=0x00000041).

    Использование:
    "imgRePackerRK.exe [options] <name[.ext]>"		- распаковка (Windows)
    "imgRePackerRK.exe [options] <name[.ext]>.dump"	- запаковка  (Windows)
    "imgRePackerRK.exe [options] <name[.ext]>.cfg"	- запаковка файла 2-го слоя (Windows)
    "./imgrepackerrk [options] <name[.ext]>"		- распаковка (Linux)
    "./imgrepackerrk [options] <name[.ext]>.dump"	- запаковка  (Linux)
    "./imgrepackerrk [options] <name[.ext]>.cfg"	- запаковка файла 2-го слоя (Linux)

    Опции (в скобках указано имя в ini-файле и значение по умолчанию):
    /log	- создавать log-файл (log = 0);
    /debug	- писать отладочную информацию, работает только с опцией /log (debug = 0);
    /quiet	- отключить вывод в консоль (quiet = 0);
    /mono	- включить монохромный режим (mono = 0); 
    /md5	- игонрировать ошибки md5 при распаковке или
		  не добавлять контрольную сумму md5 при запаковке (md5 = 0);
    /rkcrc	- игнорировать ошибки RockChip CRC (rkcrc = 0);
    /rkaf	- создавать RKAF image при запаковке (rkaf = 0);
    /skip	- пропустить проверку размера файла образа прошивки; используется при распаковке 
		  (skip = 0);
    /2nd	- распаковка/запаковка файлов второго слоя (2nd = 0);
    /cid	- не проверять ChipID (cid = 0);
    /rmd4	- выравнивание ramdisk в Android Boot image по границе 4 байта (rmd4 = 0);
    /symb	- игнорировать ошибки проверки символьных линков (symb = 0);
    /bcpath:<path>
		- базовый путь для конфигурационных файлов RKAndroidTool;
    /lname:<[path]name>
		- название загрузчика для конфигурационных файлов RKAndroidTool;
    /ini	- перезаписать ini-file с опциями из командной строки (-);
		  Примечание:
		  Опции командной строки всегда имеют приоритет выше параметров ini-файла.

    Примечание:
    Для распаковки/запаковки gzip/cpio файлов Windows-версия утилиты использует внешнюю библиртеку
zlib1.dll (http://www.zlib.net/) и собственный упрощенный алгоритм распаковки/запаковки cpio (впрочем, 
аналогичный, судя по результату, оригинальному). Linux-версия использует вызов внешних нативных 
утилит gzip/gunzip и cpio (поэтому простая перепаковка без изменений не дает прямого совпадения
полученной прошивки).

    Используемые коды обозначения типов файлов:
	-1 - не определено;
	00 - Unknown;
	04 - Android boot image;
    	06 - ext3 image;
	11 - RockChip KRNL signed file;
	12 - RockChip PARM signed file;
	14 - gzip/cpio archive file;
	15 - RockChip bootloader image;
	16 - ext4 image;
	17 - cpio_bin_odc archive file;
	18 - cpio_ascii_odc archive file;
	19 - cpio_ascii_new archive file;
	20 - cpio_ascii_crc archive file;
	30 - Rockchip resources image file;
	39 - Rockchip uboot image file.

    Состав архива:
    1. imgRePackerRK.exe	- Windows-версия.
    2. zlib1.dll		- библиотека поддержки gzip-файлов для Windows-версии.
    3. imgrepackerrk		- Linux-версия.
    4. ReadMe.txt		- этот файл.
    5. ReadMe_utf8.txt		- то же самое в кодировке UTF-8.

===================================================================================================

    Download:
    http://4pda.ru/forum/index.php?showtopic=457790          (rus)
    http://forum.xda-developers.com/showthread.php?t=2257331 (eng)

===================================================================================================

    Special thanks:
	Jean-loup Gailly & Mark Adler 	for zlib library (http://www.zlib.net/) 

===================================================================================================

History:
1.06 [W&L] (03.05.2017)
	+ добавлена поддержка формата RockChip uboot;
	+ добавлен метод DirtyBlk;
	+ поддержка старого формата RKFW;
	+ поддержка RK???? (ChipID=0x00000021);
	+ поддержка RK33xx (ChipID=0x00000041);
	+ при неопределенном в parameters размере файла устанавливаем в прошивке 0;
	+ создание файлов с размером = 0;
	+ проверка/пропуск BOM;
	+ добавлено определение OS;
	+ добавлен ключ /rmd4;
	~ улучшен алгоритм чтения bcpath и lname;
	~ мелкие улучшения. 
1.05 [W&L] (10.08.2015)
	~ использование WinAPI для создания каталогов;
	+ поддержка формата Rockchip resources image;
	+ поддержка RK32xx (ChipID=0x00000080);
	+ добавлен ключ /symb;
	+ добавлен ключ /bcpath;
	+ добавлен ключ /lname;
	+ создание конфигурационных файлов для RKAndroidTool v.1.xx/2.xx;
	+ проверка "пересечений" разделов и "дырок" между ними;
	+ сравнение длины файлов с размером раздела. 
1.04 [W&L] (17.02.2014)
	+ распаковка/запаковка "одиночно стоящих" PARM-signed файлов;
	~ изменен алгоритм распаковки KRNL-signed файлов (отрезаем "лишнее");
	~ усовершенствован алгоритм автоматической коррекции ошибки описания размера области,
	  отведенной под отдельные файлы;
	- удален ключ /blk;
	+ мелкие улучшения.
1.03 [W&L] (21.01.2014)
	~ исправлен баг проверки symlink-ов с абсолютными путями (CPIO);
	+ добавлена автоматическая коррекция ошибки описания размера области, отведенной под 
	  отдельные файлы;
	+ добавлен ключ /blk;
	+ добавлен ключ /cid.
1.02 [W&L] (03.10.2013)
	~ исправлен баг с распаковкой/запаковкой "одиночно стоящих" KRNL-signed образов.
1.01 [W&L] (01.10.2013)
	+ добавлена поддержка формата nongzipped cpio_ascii_new archive file;
	+ добавлен ключ /skip.
1.00 [W&L] (06.09.2013)
	! Release;
	+ добавлена поддержка формата gzip/cpio archive file;
	+ добавлена поддержка формата cpio_ascii_new archive file;
	~ оптимизированы некоторые участки кода;
	- удален ключ /inter;
	- устранены мелкие ошибки в коде;
	+ мелкие улучшения.
0.95 [W&L] (26.05.2013)
	! pre-Release #5;
	+ добавлена поддержка формата RockChip bootloader image.
0.94 [W&L] (17.05.2013)
	! pre-Release #4;
	+ добавлен ключ /2nd;
	+ добавлена поддержка формата Android boot image.
0.93 [W&L] (29.04.2013)
	! pre-Release #3.
0.92 [W&L] (21.04.2013)
	! pre-Release (for internal use).

===================================================================================================
