# Установка и настройка PHP

Ты можешь установить интерпретатор PHP себе на компьютер. Это позволит тебе запускать у себя программы. В отличие от сервисов типа ideone, ты можешь запускать программы без ограничения по размеру и времени работы, можешь читать/сохранять данные в файл, можешь работать с сетью и интернетом. 

В этой инструкции упоминается командная строка. Если ты с ней не работал, надо почитать мой [гайд по командной строке](cli.md) или любую другую статью.

Обрати внимание, на Windows XP можно поставить максимум PHP5.4 (и Apache 2.2). Для более новых версий надо обновиться.

Обрати внимание, инструкция ниже немного устарела. Теперь страница скачивания бинарников под Windows находится тут: http://windows.php.net/download/ x86 — версия для 32-битной ОС, x64 — 64-битная версия (она не очень проверенная, если не заработает — придется ставить 32-битную). Из Thread Safe и Non Thread Safe выбирай Thread Safe (c поддержкой многопоточности).

![Как установить PHP на компьютер, часть 1](http://i.imgur.com/K7NPy22.jpg)

![Как установить PHP на компьютер, часть 2](http://i.imgur.com/muRL2gr.jpg)

Вот, таким образом ты можешь установить PHP и запускать скрипты из командной строки. Учти, что во многих IDE (PhpStorm, Netbeans PHP) эта возможность уже встроена и в них программу можно просто запускать нажатием одной клавиши, надо лишь правильно указать путь к интерпретатору PHP в настройках редактора.

Также, тебе может захотеться запускать программы на PHP не только из командной строки, но и через браузер. Для этого нужен *веб-сервер* — программа, которая взаимодействует с браузером и отвечает на его запросы (веб-сервер принимает запрос на загрузку страницы от браузера и запускает нужный PHP скрипт, а результат работы отдает обратно в браузер). Обычно для этого ставят Апач, но для начала тебе вполне хватит встроенного в PHP сервера. Чтобы запустить его, перейди в папку со своими PHP файлами:

    d:
    cd \phpfiles\my\files\
    
(Естественно, надо подставить в эти команды имя диска и папки где у тебя на самом деле хранятся файлы). После этого запускай PHP в режиме сервера (то есть он запустится и будет ждать запросов от браузера): 

    "c:\php\php.exe" -S localhost:9091
    
`-S` обозначает «запуститься в режиме сервера». Надо написать именно заглавную S, c маленькой буквой не заработает. `localhost` обозначает принимать соединения только со своего компьютера, и не принимать соединения с других устройств (если хочешь чтобы твой сервер был доступен во всей локальной сети, пиши вместо `localhost` адрес `0.0.0.0` — после этого к тебе можно будет зайти по ip ~~и что-нибудь набить~~).

`9091` — это номер порта, на котором сервер будет ждать соединения от браузера. Если произойдет ошибка и будет написано что этот порт уже занят, введи другое число (от 1 до 65534), например `9092`.

После того, как сервер запущен, ты можешь запускать программы в той папке через браузер. Для этого набери в нем `http://localhost:9091/test.php` — должен будет запуститься скрипт test.php и его результат работы отобразится в браузере (а в консоли ты увидишь строчку с его названием, и сообщения об ошибках если таковые будут).

Если ты расшарил сервер на всю сеть, указав адрес `0.0.0.0` при запуске, то можешь зайти на него с другого устройства, указав IP компьютера: `http://10.2.3.4:9091/test.php`.  Если у тебя есть роутер то с `0.0.0.0` зайти можно только из твоей домашней сети, если нет роутера или ты прокинешь порт наружу - из всей сети провайдера, если у тебя подключен «белый IP», то вообще со всего мира.

Ты можешь запустить несколько серверов в нескольких консолях, если вдруг понадобится, но не забудь указать каждому свой уникальный номер порта.

Для завершения работы сервера нажми в консоли `Ctrl + C` (если ты читал мой гайд по командной строке то и так знаешь, что эта комбинация клавиш завершает выполняющуюся программу).

