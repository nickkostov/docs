Файлове, директории (папки). Контрол на достъпа.

В линукс имаме следните файлови структури:

- Блокове
- Inodes
- Връзи : Твърди и символни

Блокове:
При изчисляването блокът, понякога наричан физически запис, е последователност от
байтове или битове, обикновено съдържаща цял брой записи, имащи максимална дължина;
размер на блок.
Така структурирани данни се казва, че са блокирани (Blocked) .

Inodes:

Inode е структура на данни във файлова система в стил Unix, която описва обект на файлова
система като файл или директория. Всеки inode съхранява атрибутите и дисковите блокови
местоположения на данните на обекта.

Links ( линкове ):

Ефективно можем да ги наречем shortcuts или път към оригиналния файл.
Разделят се на твърди и символични: Hard links and Symbolic links.
Symoblic links или още така наречените soft линкове правят връзка между два файла като
пишейки в създадения със командата ln ние можем да препращаме информацията в
оригиналния.

Създаване на символична връзка и преглед:

Hard links или твърди линкове е файл който споделя същата inode структура.
Тоест за да проверите да ли имате успешно направен hard link ще трябва да проверите файловият номер с ln -i . Сега идва въпроса какви са тези номера. Този номер който ще видите използвайки командата е следствие на факта, че цялата линукс система е изградена на идеята да споделя правилото “ВСИЧКО Е ФАЙЛ” което свежда, че за да се различават тези файлове те трябва да са маркирани от системата с цел да бъдат специфични за дадената среда.

Създаване на твърда връзка и преглед:

В примера горе виждате, че символичната връзка си личи много по ясно от твърдата.
За да проверите дали inode е споделен ще трябва да проверим дали conf файла има същият
inode номер който има и файла в etc с име config2.conf.

Как изглежда:

Както виждате с командата ls -li аз правя лист с inode номера и файловете и в случая виждаме
ясно, че inode номерата на etc/config2 и на conf2 си съвпадат. Тоест това което посочва това
като факт за нас е, че данните между тези два файла се споделят и, че имат напълно една и
съща структура данни.


Права и контрол на достъпа в Линукс файловата система.
Нещата които трябва да знаете първо са следните два факта. 
Привилегийте на всички файлове с системата на линукс се изписват буквено и цифрено.

Буквено изглеждат така:

r Права за четене идва от read.
w Права за писане идва от write.
x Права за изпълняване идва от execution.

- Посочва, че няма никакви права дадения файл или папка ( директория ).

Както е казано закона под който линукс работи е, че всичко е файл тоест и директорийте.
Което посочва, че имаме и допълнителна информация посочваща това в началото на файловете и директорийте намира се най отпред на чело на правата:

- Посочва, че е файл.
d Посочва, че е директория (папка).
l Посочва, че файла е линкнат.

Цифрен формат за записване на правата (октален):

Цифрен формат за записване на правата (октален):

4 Четене
2 Писане
1 Изпълнение
0 Без правомощия

Файловете имат три типа вид на собственост – потребител, група и всички останали, за това
те имат следния формат след преглед със ls -l в всяка ситуация. За да знаете кои права за кого са, ги разделяте по 3. Първата тройка е за потребителя, втората е групата а третата е всички
останали.


Команди за промяна на правата:
chmod u+r {filename} Дава правото на потребителя да чете
даденият файл или директория.
chmod u+w {filename} Дава правото на потребителя да може да
пише по дадения файл или директория.
chmod u+x {filename} Дава правото на потребителя да може да
изпълнява даденият файл или директория.
chmod u-r {filename} Премахва правото на потребителя да чете
даденият файл или директория.
chmod u-w {filename} Премахва правото на потребителя да пише
даденият файл или директория.
chmod u-x {filename} Премахва правото на потребителя да
изпълнява даденият файл или директория.
chmod g+r {filename} Дава правото на групата да може да чете
даденият файл или директория.
chmod g+w {filename} Дава правото на групата да може да пише
даденият файл или директория.
chmod g+x {filename} Дава правото на групата да може да
изпълнява даденият файл или директория.
chmod g-r {filename} Премахва правото на групата да може да чете
даденият файл или директория.
chmod g-w {filename} Премахва правото на групата да може да
пише даденият файл или директория.
chmod g-x {filename} Премахва правото на групата да може да
изпълнява даденият файл или директория.
chmod o+r {filename} Дава правото на всички останали да четат
даденият файл или директория.
chmod o+w {filename} Дава правото на всички останали да пишат
даденият файл или директория.
chmod o+x {filename} Дава правото на всички останали да
изпълняват даденият файл или директория.
chmod o-r {filename} Дава правото на всички останали да четат
даденият файл или директория.chmod o-w {filename} Дава правото на всички останали да пишат
даденият файл или директория.
chmod o-x {filename} Дава правото на всички останали да
изпълняват даденият файл или директория.
chown {username} file.extension Променя потребителя собственик на файл.
chgrp {groupname} file.extension Променя групата собственик на файл.
аddgroup {groupname} Добавя нова група.
chown :{groupname} file.extension Променя основната група собственик на
файла.
chown {username}:{groupname} file.extension Променя потребителя и групата собственици
на файла



SUID, SGUID и Sticky bit.

SUID:
Прилагане на право на собственика което се бележи със “s” вместо знака за изпълнение “x”.
Идеята е ако имате един скрипт който трябва да се ползва от всички потребители да се
добави тази привилегия. Веднъж добавена това дава шанса на потребителите да ползват
скрипта без да са го направили. Пример за такава програмка е “passwd”.

SGUID:
Прилагане на право на групата което се бележи със “s” вместо знака за изпълнение “x”.
Идеята е ако имате един скрипт или програма, чиято група се съдържа много потребители, те
да могат да я изполват. Пример за такава програма е “ssh-agent”.


Sticky bit:
Прилагане на право на което позволява да може само потребителя създател да изтрие
даденият файл и никой друг.


su - {username} Смяна на потребителя.
mkdir {directory name} Създава папка.
groupadd {groupname} Добавяне на група.
usermod -aG {group} {username} Добавете потребителя към допълнителните
групи. Винаги с -аG ако добавяте група към
touch {filename or filename{1..-} } Създава един файл по фаше наименование
или може да направи много файлове ако
добавите преди extension на файла {1..което и
да е чило = ще отговаря на максималния брой
файлове}
useradd {username } Добавяте потребител в някой системи
интерактивно в някой не, използвайте
внимателно.
passwd {username} Променя паролата на потребител.
adduser {username} Добавя нов потребител интерактивно.
chmod -R {permissions} {folder}/ Променяте правата на папка и файловото
съдържание.
usermod -G {group} {username} Сменяте основната група на потребителя.



umask
Показва текущите настройки с които потребителя в действие ще създава папки и файлове.
Обикновенни стойности:
• 0002 за нормални потребители.
• 0022 за root потребителя.
Директорна структура:
• Обърната дървовидна структура с един корен (боаб ).
• Разграничението на малки от големи букви (case sensitive).
• Всяка папка или файл, чието име започва с . (точка) е скрита от нормалният „поглед“.
• Просто . В папката (директорията) обозначава текущата директория.
• Две .. Са предходната ( една папка назад или нагоре към първият клон).
Команди с цел откриване и локализиране:
• locate : комадна която търси в локаната база данни за папки и файлове които съвпадат
определен критерии.
• updatedb : опреснява локаната база с данни която locate ползва.
• whereis : това е команда която локализира бинарките, източници и наръчници за команда.
Командата find:



find .
Намира всичко в директорията и под неяfind {directory name} Намирате всички директории свързани с
нея.
find . –type d Ще намери всички директории без
файлове.
find . –type f Търси само файлове.
find . –type f –name {filename} Търси файлове по дадено име.
sudo find -type f -name “{filrename}*” Търи файла глобирайки го (wildcard)
sudo find . -type f -iname “{filename*}” Търси файла и премахва case sensitive
случаите.
find -type f -iname "*.txt" Може и с глобиране.
find . -type f -mmin -10 Търси последно модифицираните
файлове примера е с 10 минути.
find -mmtime Опцията която търси време дни за
модификацийте.
find -size option find . -size +5M Търси по зададен размер.
find . –empty Търси само празните файлове – без
съдържание.
find –perm 777 или 666 Търси по зададени права.
find webin -exec chown ivan:sudo {} + Тръси даден файл и му прилага права или
команда. Тук е с промяна на групата.
find webin -type f -exec chmod 660 {} + Тръси даден файл и му прилага права или
команда. Тук е с промяна на правата.



Регулярни изрази:
Регулярните изрази позволяват фина спецификация на търсенията и се поддържат от
множество популярни команди и езици за програмиране.
• grep g..m /etc/passwd .
• Точката обозначава един знак.
• ^ търси в началото на линията.
• $ търси в края на линията.
• Може определени комбинации.
• grep –i прави grep не чуствителен към знаците.
• grep ^[Aa].[Aa] /etc/passwd .
• man 7 regex .
Wildcards (file globbing) - предлагат лесен начин за подаване на множество имена на
файлове като аргументи на команди (програми)
• Wildcards се указват със специални символи:
• ? – единичен символ.
• * - нула или повече последователни символа.
• [...] – класове и обхвати {...} – списък символни низове.


Във всички UNIX базирани системи имат нещо като “кофа” за всичкият изход от
команди. “Кофата” се нарича още standard output.
Абривиацията е 'stdout' ===> Стандартен изход.


Пример:
Това което правя оттдолу е прескачане на “кофата” и прехвърлянето на информацията
от ls -lah командата във файл с име bucket.

Също можем да извършваме във една комада действието с piping:
Piping – позволява STDOUT (изход) на една програма (лявата на pipe) да стане STDIN
(вход) на
друга (дясната на pipe).
Символът за pipe е “|”.


tee – позволява едновременно запис към STDOUT и към файл.
Стандартен вход:
Стандартиният вход (standard input) е най често зададен от нас използвайки
клавиатурата – пишейки командите.
Но може да бъде и от приложение/deamon. Файлове и стандартен вход могат да се
ползват в стандартният вход на други команди:
• със <, |
• Абривиация – ‘stdin’
• Примерно wc < test.sh.
• cat /etc/passwd | less
Стандартна Грешка:
Индфикационнен номер ако нещата не са направени както трявбва.
• Абривиация ‘stderr’
• Попринцип е излиза на екрана като стандартен изход
• Има ‘файлова дръжка’ – цифра с която е свързана – 2
• stdin е 0
• stdout е 1
• ./script.sh == виждаме грешката директно на екрана
• ./script.sh 2> error.log пращаме грешката във файл
• ./script.sh 2>&1 | less == отваряме грешката дирекнто на екрана с less


Tee командата:
Командата ‘tee’ чете данните от ‘stdin’ и записва данните в ‘stdout’. Командата е много
полезна за връзване на много команди поглеждайки ‘stdout’ на различни етапи.

tr командата:
Конвертира, извлича и изтрива символи и знаци.
Примера показва трансформация от малки символи към големи.


Същия пример – друг метод на изписване:


Пример в който превръщам space в табулация:

Трансформация и записването и в нов файл.

Без опции - конвертиране от един набор символи към друг:

Sort командата:
Сортира по азбучен ред думи и др.


Пример с прехвърляне на изхода:

Сортиране в обърнат ред:

Случаен принцип:

Сортиране на определени от нас колони:

cut:
Извлича избрани полета от редове текст (използва табулация за разделител по
подразбиране). Работи най-добре със структуриран текст (текст с колони).