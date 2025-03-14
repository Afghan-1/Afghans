“Київський фаховий коледж зв’язку”

Циклова комісія комп’ютерної та програмної інженерії

**ЗВІТ ПО ВИКОНАННЮ**   
**ЛАБОРАТОРНОЇ РОБОТИ №5**

з дисципліни: «Операційні системи»

**Тема: “Знайомство з командами навігації по файловій системі та керування файлами та каталогами”**

Виконали студенти   
групи РПЗ-23а  
Команда 1: Туровський В.В.,   
Нестропа М.Р. та Мойсеєнко М.О.   
Перевірила викладач  
Сушанова В.С. 

Київ 2025  
Робота студентів  групи РПЗ-23а  Команда 1: Туровський В., Нестропа М., Мойсеєнко М.

**Тема: “Знайомство з командами навігації по файловій системі та керування файлами та каталогами”**

**Мета роботи: **

1.  Отримання практичних навиків роботи з командною оболонкою Bash.

2.  Знайомство з базовими командами навігації по файловій системі.

3.  Знайомство з базовими командами для керування файлами та каталогами.

**Матеріальне забезпечення занять:**

1\. ЕОМ типу IBM PC.

2\. ОС сімейства Windows та віртуальна машина Virtual Box (Oracle).

3\. ОС GNU/Linux (будь-який дистрибутив).

4\. Сайт мережевої академії Cisco netacad.com та його онлайн курси по Linux

**Короткі теоретичні відомості:**

**Navigating the Filesystem**  
**  **

In Linux, everything is considered a file. Files are used to store data such as text, graphics, and programs. Directories are a type of file used to store other files; Windows and Mac OS X users typically refer to them as folders. In any case, directories are used to provide a hierarchical organization structure. However, this structure may be somewhat different depending on the type of system in use.

When working in a Linux operating system, it is important to know how to manipulate files and directories. Some Linux distributions have GUI-based applications that allow you to manage files, but it is advantageous to know how to perform these operations via the command line.

On a Windows system, the top level of the directory structure is called My Computer (fig. 5-1). Physical devices, such as hard drives, USB drives, network drives, show up under My Computer and are each assigned a drive letter, such as C: or D:.

![Зображення, що містить знімок екранаВміст, створений ШІ, може бути неправильним.][image1]

Figure 5-1. A visual representation of a Windows directory structure 

Like Windows, the Linux directory structure, typically called a filesystem, also has a top level. However instead of My Computer, it is called the root directory, and it is symbolized by the slash / character (fig. 5-2). Additionally, there are no drives in Linux; each physical device is accessible under a directory, as opposed to a drive letter.

To view the contents of the root directory, use the ***ls*** command with the ***/*** character as the argument

The Linux ﬁlesystem structure originally evolved from the Unix ﬁle structure. In a Linux ﬁlesystem, common directory names are used for common functions. Table 5-1 lists some of the more common Linux virtual top-level directory names and their contents.

![Зображення, що містить знімок екранаВміст, створений ШІ, може бути неправильним.][image2]

Figure 5-2. A visual representation of a typical Linux filesystem

TABLE 5-1    Common Linux Directory Names

| Directory | Usage |
| :---- | :---- |
| / | root of the virtual directory, where normally, no files are placed |
| /bin | binary directory, where many GNU user-level utilities are stored |
| /boot | boot directory, where boot files are stored |
| /dev | device directory, where Linux creates device nodes |
| /etc | system configuration files directory |
| /home | home directory, where Linux creates user directories |
| /lib | library directory, where system and application library files are stored |
| /media | media directory, a common place for mount points used for removable media |
| /mnt | mount directory, another common place for mount points used for removable media |
| /opt | optional directory, often used to store third-party software packages and data files |
| /proc | process directory, where current hardware and process information is stored |
| /root | root home directory |
| /sbin | system binary directory, where many GNU admin-level utilities are stored |
| /run | run directory, where runtime data is held during system operation |
| /srv | service directory, where local services store their files |
| /sys | system directory, where system hardware information files are stored |
| /tmp | temporary directory, where temporary work files can be created and destroyed |
| /usr | user binary directory, where the bulk of GNU user-level utilities and data files are stored |
| /var | variable directory, for files that change frequently, such as log files |

The common Linux directory names are based upon the Filesystem Hierarchy Standard (FHS). Many Linux distributions maintain compliance with FHS. Therefore, you should be able to easily ﬁnd ﬁles on any FHS-compliant Linux systems.

When you log in to your system and reach a shell CLI prompt, your session starts in your home directory. Your home directory is a unique directory assigned to your user account. When a user account is created, the system normally assigns a unique directory for the account. You can move around the virtual directory using a graphical interface. However, to move around the virtual directory from a CLI prompt, you need to learn to use the ***cd*** command.

To navigate the filesystem, use the cd (change directory) command.

cd \[options\] \[path\]

**Managing Files and Directories**

When working in a Linux Operating System, it is important to know how to manipulate files and directories. Some Linux distributions have GUI-based applications that allow you to manage files, but it is advantageous to know how to perform these operations via the command line.

Globbing

*Glob characters* are often referred to as wild cards. These are symbol characters that have special meaning to the shell.

Globs are powerful because they allow you to specify patterns that match filenames in a directory. So instead of manipulating a single file at a time, you can easily execute commands that affect many files. For instance, by using glob characters, it is possible to manipulate all files with a specific extension or with a particular filename length. Unlike commands that the shell runs, or options and arguments that the shell passes to commands, glob characters are interpreted by the shell itself before it attempts to run any command. As a result, glob characters can be used with any command.

The **asterisk \* character** is used to represent zero or more of any character in a filename. You can use the asterisk character at any place within the filename pattern.

The **question mark ? character** represents any single character. Each question mark character matches exactly one character, no more and no less.

The **bracket \[\] characters** are used to match a single character by representing a range of characters that are possible match characters. Brackets can also be used to a represent a range of characters.

The **exclamation point \! character** is used in conjunction with the square brackets to negate a range. For example, the pattern /etc/\[\!DP\]\* matches any file that does not begin with a D or P.

Copying Files

The ***cp command*** is used to copy files. It requires a source and a destination. The structure of the command is as follows:

cp \[source\] \[destination\]

The source is the file to be copied. The destination is where the copy is to be located. When successful, the cp command does not have any output (no news is good news). The **\-v option** causes the cp command to produce output if successful. When the destination is a directory, the resulting new file keeps the same name as the original file. To give the new file a different name, provide the new name as part of the destination. The cp command can be destructive to existing data if the destination file already exists. In the case where the destination file exists, the cp command overwrites the existing file's contents with the contents of the source file. By default, the cp command will not copy directories; any attempt to do so results in an error message. However, the recursive **\-r option** allows the cp command to copy both files and directories:

cp \-r \[source\_directory\] \[destination\_directory\]

Moving Files

To move a file, use the ***mv command***. The syntax for the mv command is much like the cp command:

mv \[source\] \[destination\]

When a file is moved, the file is removed from the original location and placed in a new location. Moving files can be somewhat tricky in Linux because users need specific permissions to remove files from a directory. Without the right permissions, a Permission denied error message is returned. The mv command is not just used to move a file, but also to rename a file. If the destination for the mv command is a directory, the file is moved to the directory specified. The name of the file only changes if a destination file name is also specified. If a destination directory is not specified, the file is renamed using the destination file name and remains in the source directory. Like the cp command, the mv command provides the following options:

| Option | Meaning |
| :---- | :---- |
| \-i | Interactive: Ask if a file is to be overwritten. |
| \-n | No Clobber: Do not overwrite a destination file's contents. |
| \-v | Verbose: Show the resulting move. |

Creating Files

There are several ways of creating a new file, including using a program designed to edit a file (a text editor).

There is also a way to create an empty file that can be populated with data at a later time. This feature is useful for some operating systems as the very existence of a file could alter how a command or service works. It is also useful to create a file as a "placeholder" to remind you to create the file contents at a later time. To create an empty file, use the ***touch command***. Notice the size of the new file is 0 bytes. As previously mentioned, the touch command doesn't place any data within the new file

	

Removing Files

To delete a file, use the ***rm command***. Note that the files were deleted with no questions asked. This could cause problems when deleting multiple files by using glob characters. Because these files are deleted without question, a user could end up deleting files that were not intended to be deleted. As a precaution, users should use the **\-i option** when deleting multiple files.

You can delete directories using the rm command. However, the default behavior (no options) of the rm command is to not delete directories. To delete a directory with the rm command, use the **\-r recursive option.** 

You can also delete a directory with the ***rmdir command***, but only if the directory is empty.	

Creating Directories

To create a directory, use the ***mkdir command***	

**Завдання для попередньої підготовки: \- Виконав Туровський Вадим**

1. \*Прочитайте короткі теоретичні відомості до лабораторної роботи та зробіть невеликий словник базових англійських термінів з питань призначення команд та їх параметрів.

   **Словник базових англійських термінів**

   * **Filesystem \- file system**  
     * **Directory \- directory (folder)**  
     * **Root directory**  
     * **Home directory**  
     * **Command line**  
     * **Move (mv) \- move**  
     * **Copy (cp) \- copy**  
     * **Delete (rm) \- delete**  
     * **Create (mkdir, touch) \- create**  
     * **Permissions \- access rights**  
     * **Recursive (-r) \- recursive mode**  
     * **Verbose (-v) \- detailed mode**  
     - **Interactive (-i) \- interactive mode**

2. На базі розглянутого матеріалу дайте відповіді на наступні питання:

   1. Порівняйте файлові структури Windows-подібної та Linux-подібної системи.

* In Windows, the main level of the file system is ‘My Computer’, where each physical drive has a separate letter (C:, D:, etc.).


* In Linux, the root directory is ‘/’, and all physical devices (hard drives, USB drives) are connected to specific directories in the file system (for example, /mnt or /media).


* In Windows, the main system files are located in the ‘C:\\Windows’ directory, and in Linux they are distributed among /bin, /etc, /lib, /usr, etc.

  2. \*Розкрийте поняття FHS. Як даний стандарт використовується в контексті файлових систем? 

* The Filesystem Hierarchy Standard (FHS) is a standard for organising the Linux file system.


* FHS defines the main directories and their purpose, which allows you to store files in specific locations regardless of the distribution.


* Compliance with FHS provides ease of navigation and simplifies system administration.


* For example, configuration files are stored in /etc, while executable files are stored in /bin and /usr/bin.

  3. \*\*Перерахуйте основні команди для роботи з файлами та каталогами в Linux: створення, переміщення, копіювання, видалення. 

* Create files: touch filename


* Create directories: mkdir directory\_name


* Moving files: mv source destination


* Copy files: cp source destination


* Recursive copying of directories: cp \-r source\_directory destination\_directory


* Deleting files: rm filename


* Delete directories: rm \-r directory\_name or rmdir directory\_name (if empty)

3. Вивчіть матеріали онлайн-курсу академії Cisco “NDG Linux Essentials”:

* Chapter 7 \- Navigating the Filesystem

* Chapter 8 \- Managing Files and Directories

0. Пройдіть тестування у курсі NDG Linux Essentials за такими темами:

* Chapter 07 Exam

* Chapter 08 Exam

0. Підготувати в електронному вигляді початковий варіант звіту:

* Титульний аркуш, тема та мета роботи

* Словник термінів

* Відповіді на п.2.1-2.3 з завдань для попередньої підготовки

**Хід роботи:**

1.  Початкова робота в CLI-режимі в Linux ОС сімейства Linux:

1. Запустіть операційну систему Linux Ubuntu. Виконайте вхід в систему та запустіть термінал ***(якщо виконуєте ЛР у 401 ауд.)***.

2. Запустіть віртуальну машину Ubuntu\_PC ***(якщо виконуєте завдання ЛР через академію netacad)*** 

3. Запустіть свою операційну систему сімейства Linux ***(якщо працюєте на власному ПК та її встановили)*** та запустіть термінал.

0. Опрацюйте всі приклади команд, що представлені у лабораторних роботах курсу ***NDG Linux Essentials \- Lab 7: Navigating the Filesystem*** та ***Lab 8: Managing Files and Directories.*** Створіть таблицю для опису цих команд

 Виконав Туровський Вадим

| Назва команди | Її призначення та функціональність |
| :---- | :---- |
| pwd  | Визначає місце знаходження користувача у файловій системі, показує поточну робочу директорію (print working directory) |
| cd Documents | Команда **cd** здійснює перехід до каталогу, який у неї вказаний як аргумент. В даному випадку це каталог **Documents** |
| cd .. | Перехід на один рівень вище у файловій системі. |
| cd / | Перехід до кореневого каталогу. |
| ls | Вивід списку файлів та директорій у поточному каталозі. |
| ls \-l | Вивід детальної інформації про файли та каталоги (права доступу, власник, розмір, дата зміни). |
| ls \-a | Вивід усіх файлів, включаючи приховані (файли, що починаються з .). |
| ls \-lah | Вивід файлів у детальному форматі, включаючи приховані файли, з відображенням розміру у зручному форматі (KB, MB, GB). |
| cp file1 file2 | Копіює файл file1 у file2. |
| cp \-r dir1 dir2 | Рекурсивне копіювання каталогу dir1 у dir2. |
| mv file1 file2 | Переміщує або перейменовує file1 у file2. |
| mv file /home/user/Documents/ | Переміщує file у каталог /home/user/Documents/. |
| rm file1 | Видаляє файл file1. |
| rm \-i file1 | Видаляє file1 після підтвердження користувачем. |
| rm \-r dir1 | Видаляє каталог dir1 та його вміст рекурсивно. |
| rmdir dir1 | Видаляє порожній каталог dir1. |
| touch file1 | Створює порожній файл file1 або оновлює його часову мітку. |
| mkdir newdir | Створює каталог newdir. |

**Примітка:** **Скріншоти** виконання команд в терміналі можна **не представляти**, достатньо **коротко описати команди в таблиці**.

0. Робота в в терміналі (закріплення практичних навичок) **обов'язково представити свої скріншоти**:

* Визначте ваш поточний робочий каталог;

* Перейдіть до кореневого каталогу та визначте Ваш поточний робочий каталог (дві команди);

* Перегляньте вміст поточного каталогу у довгому форматі (скористайтесь відповідним ключем команди ls);

* Перейдіть до каталогу /usr/share та визначте Ваш поточний робочий каталог (дві команди)

* Перегляньте вміст поточного каталогу включаючи і приховані файли (hidden files) (скористайтесь відповідним ключем команди ls);

* \*Перейдіть до каталогу /etc;

* \*Перегляньте вміст даного каталогу, але щоб виводило тільки назви файлів, що починаються з літери вашого імені;

* \*Перегляньте вміст даного каталогу, але щоб виводило тільки файли, назви яких складаються з 6 літер;

* \*\*Перегляньте вміст даного каталогу, але щоб виводило тільки файли, назви яких закінчуються на літери ваших імен, наприклад якщо ваші імена Ivan, Anna, Maks, то вибірку робиму, щоб назви файлів закінчувались на літери \[i,a,m\];

* \*\*Перейдіть до домашнього каталогу поточного користувача та перегляньте його вміст у рекурсивному (зворотному до алфавітного) форматі (виконати цю дію через конвеєр команд);

* В поточній директорії створити директорію з назвою вашої групи;  

* Переглянути оновлений вміст домашнього каталогу поточного користувача. Скористайтесь ключем \-r команди ls, яку інформацію ви отримаєте?

* Перейдіть у створену вами директорію з назвою Вашої групи та створіть у ній порожній файл *lab5*

* Створити в даній директорії 3 директорії з прізвищами студентів вашої команди *surname1, surname2, surname3* (команда mkdir мульти аргумента, тому всі три каталоги можна створити однією командою);

* Перейдіть у перший підкаталог *surname1* та створіть порожній файл з ім'ям першого студента *name1*;  

* За допомогою команди *echo "Hello, my name is Name1" \> name1* внесіть у цей файл дані про студента (символ *\>* дозволяє вивід команди *echo* перенаправити одразу у файл *name1*;

* Перегляньте вміст файлу *name1* за допомогою команди *cat name1* (має містити щойно введену Вами інформацію)

* Зробіть копію першого файлу *name1* та перейменуйте її у файл з другим ім'ям студенту Вашої команди *name2*;

* Перегляньте вміст каталогу, обидва файли мають з'явитися; 

* Перегляньте вміст другого файлу *cat name2* (він має поки що містити повну копію вмісту файлу *name1*)  

* Замініть зміст файлу name2, щоб він містив відповідне ім'я другого студента за допомогою команди *echo "Hello, my name is Name2" \> name2*

* Перегляньте вміст другого файлу *cat name2* (він вже має містити оновлену інформацію)

* Перемістіть файл *name2* у директорію *surname2*;

* Зробіть копію першого файлу *name1* та перейменуйте її у файл з третім ім'ям студенту Вашої команди *name3*;

* Перемістіть файл *name3* у директорію *surname3*;

* Перейдіть до директорії  *surname3;*

* Перегляньте вміст третього файлу командою *cat name3* (він має містити дані про другого студента)

* Замініть зміст файлу name3, щоб він містив відповідне ім'я третього студента за допомогою команди *echo "Hello, my name is Name3" \> name3*

* Перегляньте вміст файлу за допомогою  *cat name3* (він вже має містити оновлену інформацію) 

* Поверніться до домашнього каталогу користувача;

* \*\*Перегляньте вміст даного каталогу, але щоб виводило тільки Ваш підкаталог з назвою групи та весь його вміст (підкаталоги *surname1, surname2, surname3* та файли *name1, name2, name3*) до того ж файли та катлоги були відкоремлені кольорами (скористайтесь відповідним ключем \-R команди ls та не забудьте використати спеціальний glob-шаблон \[імя каталогу\])

**Примітка:** Назви підкаталогів *surname1, surname2, surname3* та файлів *name1, name2, name3* замініть на свої 

       

0. Опишіть дії, які виконують команди для переміщення по системі каталогів:

* команда cd /	

* команда cd /home

* команда cd \~	

* команда cd (без аргумента)

* команда cd ..	

* команда cd ../..	

* команда cd \-

 

**Контрольні запитання:**

1. Як можна переглянути шлях до домашньої директорії користувача за допомогою команди echo? Існує 2 способи, наведіть обидва приклади у терміналі (відповідь є у матеріалах академії cisco на сайті netacad.com)

2. \*Чи можна переглянути вміст кореневого каталогу, перебуваючи у домашньому каталозі користувача без переходу у кореневий каталог? Продемонструйте це в командному рядку.

3. \*Яким чином в терміналі можна додати інформацію в порожній файл?

4. \*\*Як скопіювати та видалити існуючий каталог? Чи буде відмінність в командах, якщо каталог буде не порожній при цьому

5. \*\*У якому з наведених нижче прикладів відбувається переміщення файлу? його перейменування? одночасно обидві дії?

* mv /work/tech/comp.png. /Desktop 

* mv /work/tech/comp.png. /work/tech/my\_car.png 

* mv /work/tech/comp.png. /Desktop/computer.png

**Оформлення звіту:**

1. Титульний аркуш

2. Тема та мета роботи

3. Завдання попередньої підготовки

4. Основні позиції ходу роботи

5. Відповіді на контрольні запитання

6. Висновки за результатами роботи **(обов’язково\!\!\!)**

**Система оцінювання лабораторної роботи:**

Виконано завдання базового рівня складності \- **3 бали**

Виконано завдання базового та середнього рівня складності \- **4 бали** 

Виконано завдання всіх рівнів складності (в тому числі й підвищеного) \- **5 балів**

Завдання середнього рівня складності позначені в завданнях (\*)

Завдання підвищеного рівня складності позначені в завданнях (\*\*)

**Примітка**: за виконання робіт в командах та оформлення звітів з використанням системи контролю версій (git) та англійської мови може бути нараховано **додатковий 1 бал**.

[image1]: <data:image/png;base64,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>

[image2]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAloAAAF8CAYAAAAXRhVcAAA/FklEQVR4Xu3dB3gc1bnG8U1C6CV0CGCqEwgdctMoNzeVNBISCD10cAFs2Rjbaxtjy5TQewgdq9gY9ybLvRfJRbItGXcwBhv3gns595zZHenom5nVSp5ZS+j/e57vkbS7s9/Z2dmZd2ZnV7EYAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAgPqgsbwAAAAA4VDyAgAAAFTvnVhlkDI/70z+3l3X17pOTF5u6rDkdQAAAEjD9OTPOcmf65I/n0r+dEMWAAAAaqgg+XNu8idBCwAAICRvWb+bQPXb5O+vJf8+VtdByd+/m7wOAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACgodo7+p9X7Rl9o0qz3O/OAgAAQCp7R9/4M58wlbL0NM3k/QAAAMCyZ9SNR8sQVYOaIe8PAAAASTosneIToDJZ/bcPuvEAOS4AAIB6b8/+D1pOyXEBAADUe3vqSNDS9ZgcGwAAQL22p44Erb2jb+wlxwYAAFCv7akuaI25Se0efn3ktXfkDR/JsQEAANRrgUFLB6ytz1+qtjzeOKO1tUvja+UYAQAA6qWgoLX16fM9IShTJccIAABQLwUFrS2dzvIEoJrVOcmSl1df6omzDpPjBAAAqHd8g9aYmzzhp0bV+Uy165MJatf8qd7r0ig5RgAAgP2uVVbr53U9VU11s6fxDVrjbvaEn5rU161jytjyaMxzXTpljw8AAKBOyGrZWqVRO+xp/ILWjtxfe8JPTWrv1g1q76Y1nsvTLXt8AAAAdYJPqPKraoPW1ucu8YSftKtd4mjW121qdzRL12B7fAAAAHWCCFTH6jrer+xp/ILWlsdqfyL87nlj1a45hWpL57M916VVXRrfaY8PAACgTrCDlrwuiCdo7cuJ8B2PSJyb1eEQ73VplhwfAABAnRBG0Nq7DyfC75rZX+1ePNlzedrVpfFncnwAAAB1QhhBa8/IG7wBKJ1qm/ykYZeTvdelWVsfbzxRjg8AAKBOCCNobX2udv92Z++2DWrvzm2ey2tScmwAAAB1xj4HLXN+Vi2/EX7nyNfVlse+77m8JiXHBgAAUGfUJmjtHXPTSW7Q2l1wndrSuXb/NieMkmMDAACoM2oTtAwdsvJN0Nrx4f95wk8Gq4scFwAAQJ1R26BlqHE3H7Ol45mrdeBZmcna+vQFi/cO/+t5cjwAAAB1yr4ELQAAAKRA0AIAAIgIQQsAACAiBC0AAICIELQAAAAiQtACAACICEELAAAgIgQtAMA3RlZW1l9atWz9GEXVkYrbQUv/3dHnNhRFURSVTnWWuSfj9MbsXXvDRlEURVEU9U0pmXsyLougRVEURVHUN7Rk7sm4LCtotcrKOk5eX5fUpRmnx5BTMZ5Wbb4nr8+0yuew1VB53f5QMW+yWk+Q12WStczMlddFbX8ur3bvVi1bXyivzwT93I/YX4/fpvu/WTEvWrc5QV4fNT3/f209H/fI66Ome55f2f+R/fY2ir1MyusySfcv2x/jsB5/5tdFrVqfYPV/TV4ftRYtWx9o9R8pr49CXVneHFlW0Gr9cNaR8vq6pC7NOD2G3IrxZLU5Rl6fae5YdNAqkNftD5XzpvVEeV0mWctMubwuavtzebV76w39RfL6TNDP/cj99fhtuv9/K+ZF60dOlNdHTc//31rPx73y+qjpnhdW9n/kcXl9ptjLpLwuk3T/8v0xDuvxl8nroqZfiyda/d+Q10dNB62DrP6j5PVRqCvLmyOratA6Sl5fl9SlGZdF0Eqpct4QtPbH8mr3JmgRtCr7E7SyCFoErUzLImjVShZBK6XKeUPQ2h/Lq92boEXQquxP0MoiaBG0Mi2LoFUrWQStlCrnDUFrfyyvdm+CFkGrsj9BK4ugRdDKtCyCVq1kEbRSqpw3BK39sbzavQlaBK3K/gStLIIWQSvT9CDy3MG0adn6UHl9XVKXZlwWQSulynlTZ4LWUnld1Pbn8mr31hv6S+X1mUDQStDz/xrr+Wgqr49aFkGriiyCFkELwfRKYmqyiuV1mZZVx4JWXaOfo+nOc5XV+i15HRqGRx999PisrJanmZLXZVKrVllHu+No2/bRb8vrv+myKoPWXoKWM455+2Mcut/mZGV8+9WiZYtDW7Vs9ZCu5npn/H/l9VHbH0ELAAAAAAAAANCgtMmfdEhQydt+k8Rzi3+v63cBdY28PQB8k3TMKz7WZ93n1u8feqa8wZ0eUK0OvSZ9J55btFiXSlEr5HRRiOcUXdA+d9rKDrqnX5mxyGmi0D636CGfeVCl5DRReSy/9BjZ26fmyOmi4tPbt9rnTTlWThuG9jlFN8tensqZ9qicbl95eqQoOW2YOuQVPyj7+ZWcLgrt8oqPiudOWydfp3bJacKmH+sP9Bhu1XWLb/Uoiiz4643K3+V8F7VFThOG9nlFjT2P06oO+dMj+Q8j+vm8W9+/fIxWFc+T04RN9/lR+7xpebpyfCpP3j4KegwrvY/dqg+KIvtQm77/8Z5+svKKNsvpwqLve4enn0/J6far9t2nXqQHtT1F7ZDThE3OoFQlpw2TfgH/SfYLKh2EGsnpwyT7BZWcLgqyZ4qaJacNm+4xyKdvYLXLKTpV3se+kj1SlZy2tjq/P/Pb8r6rq/bvjT1A3k8YZJ8UFclG3tUlf+Z3fXr6lpw2LHqnbIHs5VdyujDo++0m+wTUF3LafaHDzCqfHp56NLfoMDntvtD3+bbsEVRy2rDIPkHV6cOph8tpw9Axd/qhsldQyWnDIHtUU3vl9PtK32e2T5/AktPvF52HLTlADiygvpLThsmnX6qKbI9F3/cSn36BJacPSzynqFD2SlGR/8Nmn56pKtJ/lqrvf7lPz5Sl974frUG1lT1tHXoUnyLvP1XpPfBWrXsWHZ5OPfJR0RGyn6t9jymXyvtOs8boGluD6id72zrkFR8v7r+6WtOp+/ST0y3ZL5X2OUW3+PQLqkly+jD49AmqXf8MeY2h73ObTx/fap8z9Rdy+tqS952q5LT7Qt53NTVDTr+vdMD8oU+fwJLTh0Hf7yjZJ1XJ6feVvP/qqn1uUQd5H/tC3+fHskc1tT5es3VgG9lzn+k7TesQXLL2dPlo4sHyPsLg0yvsSuttLX27vT7Thlqypx99u2I5XbhV3Fv2TMU7feg1RvYMEq/ukHlIpTfia2Vvo1Ne0VnytmHXn0YN8ZxfsA9Bq1alV5DPyTEYHfKKTpC3jaDSetshnldU5DNtmFVtOPOZJsxKudPic/tQy+x4yJ7tc6e1lLcLtXKmLZQ9XZ7bhl/XyZ42ff2dPtOEWS/JnpK+TZnPdKGW7GmTt42scopulL0NfV0vz20jKNl3n+g73C0bhF16g/Vv2VeS00RVsq8Uz0DQMiX7SvHIg1b1Y7DJaaMo2TNIPENBy5TsbWQiaOnaKftmOmiZkmMwMhS0TP1H9pYyELTM+utm2dcmbx9FyZ4uebsoSvaMPGglS/Y15G0iqZyit2VfVzz6oOWU7GuLZyBomZJ9XfJ20Vbxb336ZyRo6cB/guxda/EMBC1TbXOmni972+TtoyrZV4pnKGjFc6enPEk7noGgpesq2TeIz7ShV8e8orNlXz/xDAatLn1nfEf2z1DQ8iyrDTBoTZe9pUwELVOyr03eNoqSPV3ydhHVb+ye3/igleJ8tjhBK1PPgVPtc70HaeKZClq5ReH994h4hoKWrpT/Esbn9k7plbrqlD89tJJ9pXiGgpYeS62DlnxMta3sPrOulH2DyDG41TG/2HO/ta03Ry9Ma8GOpwhad7w8Wt34TGFodXbz/LjsnypoPfzOJHXXq2NCqZOa5v7Z7psqaN324kj100f7qLMe7BFePdRDnd40r/SU+7ofZI8jVdDSK0bP46ht3f7SqEV2Xz+pgpbzicO8cEr2tcm+UZTs6ZK3s6tjXnEo9XjPmfUiaMlx70Otln1d8XoQtHweT61K9nXJfnY56/Ie4VWXj2amH7T0mP/cZZB3PVbL0uu+dbray/61Eg8IWmYDevsLI9RtzxaGUjc8OXSBHvRPZX+X7G/q/jfGmQcbRQ2R/V3xgKB1UauPVSM9bVjljkX2d8V9glab7tPUUfflyMeyz3VGk9x7ZH9JjsXUdU8VeO4rnMr9QPa3xQOC1vH3hz9vrJrt9g8KWifenyunCaXcvkFB61cd+numiaAqPgzTwSdoddAruYuzPpLThFWD3N5SUNC6rPXH8j5CqPwRsr8he5sygfOYB3LVKSFVcgxL0un94FsT1HGRvBbybzc9g4KW2cie2CTPM/baVrLvquoer6mTInjtndE091d272R/36B1r94x+L4e82lNwqnkGN6V/Y14QNBq1Dzf8xjCKJ/+nt4mmFnPWfjVJK/i/zLGfYKWWf/Y29Wwy378tRL3CVrtc6apkyKaaY2a5GXJMRhyDKZOjGgMicr9HzkGI+4TtFq+O8ln+nBKLxy+Jz/GfYLWuQ/39EwfVsn+khyLCeKnVq4QQi/Z3xb3CVrt9DIr7yPscvv7Ba1/Ph1V6HTKOSE5KGiZFbzPNKGX+/j9gtZDb0/03D7MOqNp3jluf5tf0PpRdIHPd7mU/c1K3wQOOW0o1ST35VS9TR0XQehwy/T0C1qJoN3Lc/tQqln+B6ke78/b9/NOE1JVzOjK/p6gZR67FY5CrTOa5H3kMwZP0Grz4VTPtGHVGc3ymoj+nufgpmcKPdOFXY2a5zifSI77BK3mb4733D7Msh9/rcR9glZUIcuqZj7jqDIGsyH3mS7MWiDHYMR9gtbpibdQIis5BiMugpZ5+2J/BRtDzpM/dhnkuY8wS/a3xX2C1t0vj/LcR9jl9vcLWsdEuHHT5XzyzC9omeXC5/aRlPv4/YLWeS2i2wkwpXdI7nL72/yCVpTBUwe+lp4xiP4PRhw6U/U2Rxbk7cMs09MvaDX7T2TvPjgV9HjNUbSTI3y+dcir8snbuE/QevCtzD3fyTF4gtY1nQd4pguzRP8qvU19L5IjqFVLh84Hk/09QeuiR6I4gl1Z9uOvlbgIWiadyyahV7M8z3kvcsa1fn+Kd7pwq7McgxEXQcsEvhMjXojkGIy4J2hF+7zI/pJ8fs5OvIcdWcn+trgIWiZsHB1t0HHK7e8XtBpFdQTDVLO8B0xf/6AV7XJhl/v4/YLW9yPcCTB1ZtMc308AyaBlgkaUz8XJnQd4Phwh58XP2/T2TBdmpeptzmuRtw+zTE+/oPWbxzOz4yX7NnlzQqTPd6NmPc6omNmJ/p6gdX7EOxl2/+QYPEHrmAi3UXonZ6XoX6W3qSjftnNLB63Tk/09Qeuoe6N7/Kbsx18rcRG0MvEWzJnN84/xGUeVGdf0jbGe6cKsU1rlfU+OwYiLoPWYXnFFeSTJlByDERdBK+ojfLK/JJ+fE6Lci2yaejxxT9AqjuTcNVluf7+gJW8bZjVq3sN528wvaN2RgSN5brmP3zdo7aflQQatqJ8L2d+Q/RtHuxNS5b90yN63vzxa3j7UMj39gtaB93T33DbEqvg+O9n3uieGytuGWpVzuqJ/laBldvLOahbNuVHJWuMzBk/QivSoXtO8h0X/Kr2rO6qe7rohdnfqZahRk9Fuf0/QOmU/bKNrJC6CVnUnoF/aupeK3Vv5oIL2Jn6c4jwJOQZDzrigQ4Emucfu6p5yxp5mjckk7Wc+8r5/Lfu74iJoXfdk6hfyXzolzg8wPVOdl3Fl2z7+b8k2z79bjsGIi6B1xytjvNNW3EcPdctTgyv+9ltgz2v5kYoFH/Wp9l8s2WPxO/HQ9Ly6Ta8q874mZZ7P7z1g3V8KcZ+gJccj6+5nC9SpTp88dbx+Hv7Ysa9nmlavjkh1XmCZ218GrVRHEWJ3fKj+9dwwdaDe4zpfvyY+mrSo4rqj9fPW+qVhKpZ83K3073793b5+Qev3nQdWve1tH6rYvz7w3Idfbd29V9311CDf5XLHrj1VLm/UPPc8dxwyaFX3dtUPm+c7811ebpccw21PVjlCEvifIGTQSnWuxhF6+T/N54Rhezkwy+91jwd/uED2N+Rz4vccuvdd29dHRTXLq/IdT7J30NG0A/RjPzVFb3t9eriZTwG3NT39glbQxjR2T+UO0MHV7AzFgsNaj6DHe36K88LM83p1G//tiFvHNU39nFTO6Yr+VYKW+dBDOiHHrHPkZWlVk9w3fcZQJWilOqr9wDNDUj4+u+56suq6pLJyLxD9qzwH5mCEd5rKWv/1dnVkdc/9gz3Vm0Nney63quL/HMdF0HKOYntvX1ELv1jnu020a8Gy1anuw/eLq2skLoJWqsOgsfvz1Ni5X6i9SlVctnXHLs/tzICLyz73XJ4s3298ljPuGJ8nxtzv2JlL1ZWPD9IbsA8qjjS558eYlbW5zR+yB6vY7YmNTeyO7s7Grsp9NfPuJbjiImhdoQOSHIdbpt9HIxILR0xvSB/WG0p5G7dKF33luczUuQ/18P1ns3ERtP6ndfAKZcWGbc6CZMbwPT3ftu/c7WzYzN/uSuDLdVsCFyR9+Xuyv2SPxZQ9vemzfutO9fHwEvVd/bvbx155u8+V32WmBk38pDK0N8tfLvvb4iJoXVPN2xbmeSqcskD99bF+6iQdbv6RPUgVL/xKHWUdbj9Yj/u2F0d4pnVLP6ZX3f4yaN31qv9RhNidH6qde5R6o1+x3jnQAei+XGW4G5+9+oUUu/l9pTONs/PQ7SP/o8luXxm0zApWvk5WbtzmzGPznDh1f+J3s7I1/Y/Ufx+r58ehOtw5Y7k78XyZv092X08P9XTGbt/vaQ/kV/xHCBm0st6b7BmzW+bTb9v08mh+d59fd8Vv+rq/r163uWK5MeM0O3SV95Pv+4ERQwatP3Yb4hmDW2WfrnY25ocl55l5bRypx/fAcwUqZ3BiY/HvnAnqmo7BJ1fL/oZ8TuQ0bo0r+axK8EhVsds/rFiHiaryL5rs3qZOCNiZWr5uqzpWX3fU/Yl1pLvhO1D/NG/7rt+6ywmIJhAULfRfV+laanrKoJVqR6fk07UVbyuv27zNeUxmvt/zetUdR2fdXvalZ/rkdRcGPV4Z0O2KPdTLeZzmMZ7WNHFk5fDk43Z/Lvlqk2c6qzxfmBsXQeueV8cEPna3Hn9rtPpdp+Dwnqp+2mKI31vVVYKWOU9NTmfKLOuxv7+rHvzPaGc+ue9CmPWB+Wk+NOF+cMK83s26SN6Hc523f5Xn4B9PBL/mzHbpKL3Ovf2ZAmcdt2bD1+q+V0aqHXqdMGzGUjWp7Atnx3Dxyo2pT/9okveO1b9q0Ap4/G7/k1v0UkOLlzg72mYMUz5Z4cyb658tVINnfKbOf7SP+k7Ktx5zK3rXWlwErVR7PVPKlqsT9UwzQevpnlOdGXT/q6PUv14Yrn4R71exco7d8K6K3eq7kjAzzPORWUMuOH5HrMxKavqiVeoqvWH9VD8xU+cuU7/pMlAtW73ZGUvJ4q/UC32K1TU6aJV/scG5j/Klqzz3o+sD2d8VF0Er1VtksX++px9zd9VKL8hdcyY5QSunoES1f2ec+njkHGfP8L1BM/TY9EJ803ue6Z37CBAXQSvo7QgTVtq+N8FZQS5ZtVmd2vIjtXvPXnW33nhs3LZLjTUrd/28/L69/56uqUZNu18s+0v2WEzZ01/7+AD1fI9JTtAqKlumckfMcd7Km7Vwher8wQTVo7BUTf/kC9XpnbGqVD9HB+v5crxe+EsXrnRWwmZjW7ZsbeV9Nsn7sexvi4ugdeWjwWHYVOy+fOd5+lvn/uqIZvnq4ZcLnaBVpJcfs1E3t+n64QQnJMpp3Trr/h4Vb3fLoHVdt8qjiXa1fWuM08sErXNaf6zmLl/vhBvjhn8XqD06aU2f94W6qkM/1a37RNXh/Qnqxm7e0Oj2lUGrXfdpVcKqWXm0eHWE+tOTQ9VavRdpzPt8rbMz9ODro9RS/ZpZumK9Gl/6mVr61Ubn+o06IMdufE+Nn7lEfTAssdMwa/Eqz16wOwZDBq2H/jvBM2a3HnxtlPqzHk+H98ar8bOWqiYvFurHvNyZ173HlDk7ZP+rN0Ir12xSM8s/d5bjPhMXVDlKYPeWZNA6wmcHzZQJEW/2LXI2Mp/rnY5zdJgsnLVMrVi/Vd3zzFC1WG9wTRBcsmJDYFjR5fm2fsPub45w+Ezn1OBJn6hTdN8H9DwxG/3GrXurs5rnqyavj3Z2Bs2RzQva9XVuO0bvUJpwIO/j1Ptzq/yTcLu3Kb+jK2YZeUgvF3M/X6/m62Xwye4T1Gd6nXm0vu2qTdtVll5Gzc/HehY7r4d/5/sH50ZNc7uanjJoBZ3WYJbHK9rqx6h33nsOn63WbNyqXugx2dn4Xdimt3q5d5HqN2Zu4ra67zkBn6oOerzme9LkcmrXEr28mx2Jpau/Vn/pPEBNKf9CDSxe6mwrFunn2XwdQdBr16lmeZ5/ARMXQetvabx1uV4HTBN0nv+4yHmOT9GXPfzmGHWafry3Phe8c25K9jfiImi1Cjif+YkPxjvPwfwVG1Wn98c7oaZb7mT15cbtzjZ6pt75n/f5Oico5up1dNB5lj79qyxzf3w86EiYXuanLnJeV81eGeEs4zt1wJqlX/+x5j3VpHkr1F16O2WWh8tTHNBIVOL0iWT/KkHrvteCTzN6sU/i0/Ff6tf5a4NKEju8v31TvV0wWy3+cr2K3faBmmtve3xKzx/Pt9PXWNwKWua9Vr+AY8rs8d+tk6j53QSt2D/fVbv1L6bW6hdQ7K/vOCtu88R+vWOPZ/qKQTfJPVSOwbBn3J0BewmzP1vn7BGZoGWenE9XbnD6m9ResuBLdXWrnmrt+q/V8Y/0dWbonU8PUW3/43MOS5PcK2R/V9wKWuaFHHR+lllhr9m0zfl9mF6BmqT8rycGqjy9Zzy2aIF6uf9MdfOLI9WTeZPVQv2Cl9NX3E+AuAhafitQUy/0nOJsnGI3faCKFq1WecNKnCMIsX+YsJvYQ5k6z39P0a1GD/Tw7DVJ9lh+9VjlC8u8iMzG3PzuHtEq0QGrbMEXzpjnLlunlq/a4CwX5qiXWbBve67QWVYGTpqv56OeBw9/JI465h4n+9viImgdH7xhdJYj93kyQcus6N7oP8MJWubIxs7de5wV7sTZn3mmtcvuL4PWaT7naJgNwIjixc7vJmhdrMPgopWbEq+RG99Xa/We3V4dtMxy6jIBedfeyqPFydri9pVB645XKo+kmR2keZ+tdn7/g97DnK+fk/5TFjmvk+U6WGzcukuH4M/V6OmLE2PQy6uxdvN25zbzP/0qcbn+/fBH5Eovv7v9+GXQatzS/zQBM6apeufMrFMGFi1xnmOnh34N36KXgRXrtzhHHMzblF+t3eQ8V4fov+95reoRQru3JINW0BGOl3onAlDLFwuccXw0foETLi7Xz8u/nhriHNGKPZDvPB9yWqsGy/6G3b9FwCcOH39vnLNM9J60UD/+951A9emX69Tt/x7qHEkwlq/a6MwPc+Tpzmf9N8CpevsdTTPzdNjUBU7v7ebIqQ4eevWsLu/QX3XuMU2dr3cAjDWbdzi3mbHYd8c0Uc3zjjY9ZdBqFhC0l+swZ352fX+c6jVqjn4dbnXWSbPnLVMt352otunnPfbnt5wdwa82bPVM71bQ4+0UEPCcaXSYMs/nSffnOEfLb9bPcdYrw535UbpklTpZ/5ypN/hyOrtOaZZb5Yt6k/2rBK0TUgQ9ZxzNeiQ27no8BdMWOTt8JUvXqHeHlqgZepv1bE7wW93O9D7iImhd5RNSzGusz9hy54jyg2+MTswPva5dtW5z4ujVbd31cveB6j52vnP0tGt3/+XWbwx2b7PMHR2wc2OOEt35TCKInqXXEblDZ6oxsz5VucPnqMklS9XU+SvV1fG+atlXGzzTyhL9qwSt6wO+z/E4vS54tXfiXQKz3l+sA+canQ/MQaGh+rl4dfDsxA7Onf7j9+tda/EqQSt4wZ1etqxi72Gn3iA89tZoteHrbXqvXK+szQsoubIYbw4F/tP/6E2qQdsz7pdx76F7c45LrGlij+ennQY6vTZu3aHeHjTT+T12e2LDsXKtXpBuSYzFBDG/wCZ72+J20EoxP/J1oIndl/h9iw42r+sntPnzBapw8nz1ykdTKjcqZqG+vlbzoyJopTo0P3HWUuenOexqfDy8VI3VC/Ojb4xy/nbeLrnTf+NT3Rhs9vNzgbXn+dDLwyve/+47slQdql90ZUtXqaP13vqAaYudUG6eExPAvt65x1kB3PvSCFVYvEQ9q/esY9e9qz5bk1ghpzueuBW0qvsOm9iNH1S8BfP3ZNB6c4AJWqtU13fHOntcL/YuDgyyyaoIO4YMWn5fVPq2DlcHJVdAT+RMVOe1+lhN0nvUn6/alAjCf3lHDZmyUO3QewrNXk/sDLxbOFc1e8nzfTTN3b4yaJ1tnW/0lN57Ncuf+f2qTv3VML0i+c+gWeoAPd8n67BjVvBf6g156aKV6p5nC9SaDVvU4uVrnFBszutat3GLWrF6o5oy93PPstaoaY+Kt24MGbSCVrQ36x0d90MKg6d/6rwWnNeEfm3c+nyh+mrjNudLZk3AnLt4pXpNv24G6/Atz/exe0t20DI7in7njJr1VvbbifBmHps5Mm+W2VU6XBQWLXbCTXbPaWr4jMRrKajOaJL/M9nfsOfFuS28odMEzt4jSp3fe01YkJgH176tZsxf4eywGX3HlKll+vnZql8j5oifvA+3UvVu6/NdSubxdngnscd/QMuPnSBqXg/X/7vACcBN/zM2sY7SG+IL25od1OBzWdyeMmj9Odv71pF598F8ga157IP0cv6VXgfMmv+lWq03dGZbcffLIxNHFPS6euDYuepAn9eQ7Ot5vN3932o3VbYosXNpgsYL/Wc5z/exyeuu1yH2fx/ppbJeTxw4CCq7rysuglZ1X9L55drEus08ZrO8tftgksruNd0JnJv19mv56pRvXb4m+xtxK2iZo4nf906n16+LK04FaNyuvzorq5c6Ti/nf9ahxBw8iP3tbRVr0VsdrJeJQdMSO4RB5dO/4vE/8v4Uz/oiqMw7POanWe7MzoRZ55pp3bdxU5XoXxG0zPo/6Ci2LLMeMP3M6RNmDGbZTHVENFH5nsdfK3EraLV8Z5JPo0TNmF95VOTZnAnqlR6TnIXn+dwJ6sn3xjobWHPZzFR7RE29T5rLfvIa+xxCNunU3Rg655uYt+OS5ztUno/1oXP+iXvZCT5HGlKNwYhbQSvVSX5mz9Q91HpDl/7qdr1R+b7u9+hrI1TXd0Y7T+hdeoN2SJPE2xZy+urGEreCVqpPgtrfX+KuJE1v5zwdPT/MRquaF0If2duP/fy4L2BTzV4aXvH7ge68T35Y4grzdrKzx5B8Szl5uZkfpn6tA8Hv2vVW17Sr+ram7C3FRdDyeUwV9XLPysPqJ+vnwrwV/BO9Afh9h76qzRsjnRf5s9Zt/EpvvKsc0bGDVtAnbr5jvfjd+W9WcOb5sE/6tX/3f9HnVvybJBm07Lf5D7s/+ARmv5JHat1p/Ta09mM3ZNAKOgreJRluTB2ZvP8zW/aqWD4vT37g5Rft+zrnmp2v/36mu/foiOxvs4NW0FtYfmV2TDZsS5w7lm7J3i57Xvi93WfKfZ32mbyocn2VfKva/G3miVnHOeda3u+dPlme81vt3s3f8s67EKviW+ntoGWW//NSfPDJrcQ3nlf9BJq7g+TOh6AKerz/iPhLMu2+rrgVtMw7HnIaWfZJ2GabZebBus3bnb/NOjDVl8vqZeJW2d+IW0HLvFWdavsSVM5pL3eknu+mGjXNH+DTv3KZCziaGXaJ/hVByxzVjOK/Ariln4PP7d61FreC1t8CDsGFWBtkf5f95Mk92rBL9rbFraD1QIpPMIVRZzTJ6yD7u+JW0DJ7DXLa0KpJXkfZ2487FrNilRvpsEv2luJW0DL/xUBOH3ad0TSvyn8R0EHrbLd/qrcvwii7rw5al2XyeXDLHoNhB63qPvETQm2V/W120Ir62+llb5fb31Q1R0YD39pMp3Tg9/zrMLv3uRF+sbLu/azb0w5aUW/odPUOeryXR/JvlirL7uuKW0Grtq/9dHeIDv/RPd+S/Y24FbSavB58flIYdWbT3DN8+lc8B6neTQivcqu8o6D7fuz2T3UwJJzyP4pdY3qw691BH3Svd2825Kry7yNs7hiqO0IRRsneNnt+XBHwUenQqkne+bK/S+8tveGO4ydtEyfIRlGyb5AMPj9LZW9Jj2OMO57rn6k8ohZVyf6G27/1B963a8KsoL7tcqrfmw6r5Bja5E/8bsaWhyapPxHbIXd6xYbv7xHvKMreLnte+L11GVY1apZ7ik/vzaa3CbxBR9PCqe7O+VlOz7zpv3Afc5vu0S7/p4ujOm5fU7U5klOD2m73dcVzp93s9n/gP9HuiMveLr1z0c8dw5UR/5/Txi0+9IQ9+zmobscipKryn2Q65FTu6F7xaLTbaLvvPmnSs/AAM2DzSb/9eiRJryjcccjpwqwzmuT6/isPV/vcotfdJ/FMn+/cCbNkb8kdR5RHDGTPIO5Yov7G/rPu9X6ZrdQxv+RIdzzn+7zNHHbJ/kY8uYG7NsXXCexrNWqa/7FP389N36x3/T8ZFnY1apL/AzkGw53/972a4vvdQijZV2rXc8pBZhzmCN/FAd+9F1J9Inu73Hlhyme60Er2NfTjfsj0NcE7yvW37Os+3ky/fdc+r+gF9/mO8ohuo+Y5p8neLvex3xDt/zf1PHZXm5ziA90xHBLhwZFGAf/MvX1O0RDnOcgNPm0gzJL9DR14h5ox/E+0RzWr/X7JGmuXV3yWnmln6zuPoir2hlJpnzf9V02ie893e6OmPa+WPf3oJ3CceRL35TB/tdUs3/ef5NradS86zjnZMZqFeXvjh3Or/bShTc+TNeZ7Y3zuK4TK3X1Ws/TH0yGvuJEOxZui3YvPmy/72nT/Q69o2/f0M5rlNwqzTm+af6rsJd30wsjjGzXJi6xOuz/vMNlT0ivarOufLph9erO80giq7en39/R86suP3vgeo18nO06I7t+Q+IZNm1lfPBzhOVKyn61DTvEFd78y2rwWNjYKtzbp3p/Kfi7zmC9N8YWh+1qyn6tdzrRf6tf/5z7j3efS66EZurfnyKEtnld0rt7Qqwsie+zpnYCt5/+Ykx/I9TyGEGrTGU3z/yr72R4ePCbWMa/4KX3bXhHVx3pe/Ej2lQ69u7tn3bWvdZquE5q+k/a2CAAAAAAAAAAAAAAAAADqiqyWrZVb8joAAADsA4IWAABARPZ30LL6l8nrAAAA6rU6FLRK5HUAAAD1GkELAAAgIgQtAACAiBC0AAAAIkLQAgAAiAhBCwAAICIELQAAgIgQtAAAACJC0AIAAIgIQQsAACAiBC0AwH5jb4Qo6ptecvnPBKs/QQsAGhq5IaKob3LJ5T8TrP4ELQBoaOyNUKuWrXfr2kNR39AiaAEAMmt/7+0D33QELQBowAhaQLQIWgDQgBG0gGgRtACgASNoAdEiaAFAA0bQAqJlvcZmyusAAN9wBC0gWtZrbLq8DgDwDUfQAqJF0AKABoygBUSLoAUADRhBC4gWQQsAGjCCFhAtghYA1FDLlq0H6Or3TSg7aOm/+8jrv6l1y9+v+bZ8XoEoELQAoIbscELVz3r5xqcIWsgIa7kjaAFAOuRGm6p/RdBCpljLHUELANJhrTjfkNdlku5f6I5FXpdpWS1bveKO5eGsVofJ6+sCPbZOlUHraYIWMoKgBQA1VLHibNH6bXldJukxjHTH0qHTo9+R12eSHsPr7lhatmx9nLy+LsjKap3jjlFeB0SFoAUANUTQ8qonQSuPoIVMI2gBQA0RtLwIWoA/ghYA1BBBy4ugBfgjaAFADRG0vAhagD+CFgDUEEHLi6AF+CNoAWjw/j1n9mHZZbPiutr71+zvy2kAIB0ELQANWnZ56cLsshJVXXUrK5kppw1bdllpS9nXr9apv8lJI5NdXnK57C+r29xZt8rpMkH3vUyOxa/kdEAmEbQANGhyo5yqniibfZScPkyyX6qS00ah2yflh8u+QSWnzQQ5hhS1UU4LZApBC0CD5rNRDrM2yH6p+ExfXT2XZj3feV5Jjc+b0tPN8OkZXOUlN8v7iJKnf+pa16181v+kWT+RvYDaImgBaNB8Nsihl+wZRE4XQfWWPVPRt1/scx+h1i1q8bdk33TJ+4qgXpY9gZoiaAFo0Hw2rqHX42UzGsu+fuR0UZTsmUp2BoKWrtWyb7p87iv8ml1yhOwL1ARBC0CD5tmwiuoWRs0rvVP29SN7R1Ed55ccKfsGyc5M0KpR+LPJ+4morpR9gZogaAFo0Hw2rE6dN6y/uthU4YB9rksTtV32luQY3Lpryjj19/EjQqnLCgcOuqRgYLpH2AKDVrfyUvVoafE+V1tdsm+65JjceqSkSN01ddw+1926rhkz7K3Y0sm1fnsTIGgBaNDkRtrUOcP6ueEo7Jos+9vkOEzdOHGUvI9Q6oIRo78t+0vZAUHrwRlT1EU6hF6i7yeMSo5pr+xfHTkuU1kzp9r3GVrJ3kC6CFoAGjS5oTZv9UWxoXZL9rfJsTxRXuqZPsyS/aVsn6DVtGii535CrBw5hlTk2LqVle635w4IQtAC0KDJjXVXXXIDG2bJ/jY5FlNy+jBL9peyfYLWD4b199xPiLVGjiEVObYuc2fJ+wu1ZH8gHQQtAA2a3Fi3KSnybGDDLNnfJsfy4PTJnunDLNlfyvYJWhdEG7T6yjGkIsf22JyZ8v5CLdkfSAdBC0CDJjfWN08a7dnA2nVGQerzt85KfX5Xyn9CLcfyjwkj5fSh1SXD+jeX/aVsn6Blndwfel02vP+1cgypyLFdG+H80vWW7A+kg6AFoEGzN9TmHJ9zUxyxmb9+rZrz1QoVG/yxczL4i2Xet/bmbFjnuayihg88X/a3VRlLean6UYqxmOowq0jFhvZVZ+vbfUv/HLFsScV15lylgiULPdNYda7sL8mgleqcsTN1AB35xTL1h3HDPde5ZebZ6JVfeC53S/avTtXnLjgE/mn8iIojcQeOGKRO12M1f7+sn2952827dvrezyWFAy+V/YF0ELQANGgy3AS9NWaCy6BPF6vZOmj9d95sdfqwfiqraKL+fY5zmbn+h/qy/xs7zDNtxX2M6Hu47G+zx2LKBBN5H3bN3bhe/UAHh1N039iQPmrqF5+ri5LXmb9jQ/t4pnFL9vYjg1bHOTM89+PWm+WznZ5Np0+u8mlCN7SYnyY4btu9yzNtTcZks8dmQqDf/DLBuVzPJ9PffGXHEXp+xYb0dsZ388RR6nx9mRuuTVi8Z4L/pzxlbyBdBC0ADZq9sX5sTvDJ1H8bP8IJUiZUmSNaO3bvVjmLF6hFmzeqQ/WG+kAdahatX+uZriYba3ssneemPt8oNri3OqSgr7pwxGB1qQkPg3qpFV9vVpt27XLe3ly0eZNnmpqMxZBB68HiSZ77MWXCyltzS9QPdN8H9G0+/XqTMxZz2dAlC9QN4wrVa3NnqZP0baMKWubcOr8jUT0Wz1cx/bzN27RB/WR0gYoNH6iuHjdcvTh7hh7LbmUM+/xTdfGooWr0F8s809d2bICLoAWgQbM31tcFnONziA4QvT5d5Pw+aNF8Vb5mlbpQ//506XQ19LMl6kz9e9sp49SNOozJaWuysbbH8hsdCuT0dn225Wvnpx20lm/aqNbv3KlGrvhCxXQIk9PUZCyGDFqNA85Pe2pWUeKInr7+7qKJqp0OW91KitWQTxc7R9Vihf1VrE+OunXK2MiC1t16/sv7M0eq/pX8HrLXddCbaEKyHuMj0yaoJ2ZNU9uTQesfU8aoW/Vl5jp5H7UdG+AiaAFo0OyN9VUjB3s2sG5dmHx7SXzJZsXvFxZ637YStUf2luyxXGEClPc+nDJHkG4bnwiF5iiOebuwsb7s9nHD1S1jC1W/z5Z6phG1Q/b2I4OWCVI+96U26cBifpq37n49Zpjqv2yp8zbrr3QA/Fpf93N93egvP1eXjxyixn31pWf6ZM2W/atjj+3KUUPk/Tnz5OzkhxOu0+O6Wwfh8/XvLSeNdt4ibqZDWLOJo9XlwwfqwDoo5fl5sjeQLoIWgAbN3li7YSqiWit7S/ZYgs4VC6MuGzZgmuztRwYteT9hlg6sLWT/6thjOy/1pz33tYplbyBdBC0ADZq7oY76W8UvLuh/iewtVYwlxaf7wqjLCgYdInv7sYNWqk8chlGydzoyFQIvHT7gHtkbSBdBC0CDVhm0ot1Yy75+MhW0LhnSv9r/c2josRS6Y9qf35gfJFMh8PLCIcfI3kC6CFoAGrzs8llvR/it4jvO6Zl/gOzpJ7u85BYTHOKlxfI+wqzxsm8qbpi5x+dk87DqkqEDLpd905FdNusxM7Yn58323GeYJfsCNUHQAgCk1G3urB9eP2HkxTp0hF6yV23cUTTpqEsL+oVesg9QGwQtAACAiBC0AAAAIkLQAgAAiAhBCwAAICIELQAAgIgQtAAAACJC0AIAAIgIQQsAACAiBC0AAICIELQAAAAiQtACAACICEELAIAa0hvNWbqmUVQ1NTWLoAUAQM1YG0+KSrcIWgAApMNnI0pR1RVBCwCAdNgbUOfvF16mqJTV5rEucjECAAB+ZNACAABASAhaAAAAESFoAQAARISgBQAAEBGCFgAAQEQIWgAAABEhaAEAAESEoAUAABARghYAAEBECFoAAAARIWgBAIBasUMERdWgrpLLEgAAEHw2oBSVTl0plyUAACD4bEApKp0iaAEAUB13w9mqZesP5HWZZG/E5XX7W8U8ynpktrwuE3TvPXVh3uhl5E6CFgAANWAFrQ/ldZlE0ApWh4LW3QQtAABqgKBVPYJWAkELAIAaImhVj6CVQNACAKCGCFrVI2glELQAAKghglb1CFoJBC0AAGqoVVbrtrpa6/qDvC6TWrV8ZIyu0bqmyev2Nz1v9ujapcPFLHldJtSVoJXVotUFej48YpaXli1anSKvBwAAqHd0wBqla4yuInkdAADIoOxPyr6bXVayR5fyq65zS0rlNA1JqnnjlpwmbN3mzj6u6/xZ5/hW+czG8vZR6lZeeopnDBVjmXGqvD0AAA3WE+Ul98rQEFRy2rBll5deLXv6lZwuSrrfAtk/qLqWzf+WnD4Mso9/zcqV00XB29dbXctKrpfTAQDQIMmNZDU1Sk4fJp9+gSWnjYrsW13J6fdVt7KSrrJHiuohpw+THstkn55B9YCcHgCABsdnAxl2zZc9g/hMW11dl3aVl14k+6XDp2fYtVP2tOnrp/hMk6q26dqcZq3pWl5ynOwZxKdXdbXJ6lVNlS7TQe67sicAAPWaz8Yximoj+/rxmS70kj2rI6ePqCbJvq7smget2lSB7OvHZ7rQS/YEAKBekxu6qEr29SOniaZKT5R9U/FOH0l9Jvu6sjMTtOrM89N17syzZV8AAOotuaGT1S2MKi+tMxvy7Lkzfy37puKZPlnmMXWaO1M9FkJ1mjNzmezrym5gQSu7vLSJ7AsAQL3l2dCVJcLRuQX91KWFA8Kt4QNSnq8lx+HWg8WT1E2TRqubQ6hfjhraX48l7S9alWMx1XH2DO9jC6eW+PT3DVrN9Dz5gX6Owiqn/4iBh8j+NjkGt+6ZMs5zf7WtC4f1d8YiewMAUC/JjaapP40rlAEgtJL9bXIcpu7TgULeR0g1UPb3I8djQujPRw6W9xVeDRtQ5d/UZPsELXM07RI5XUhl95bkOEzFZ0/33EdYJfsDAFDvyA2nKfeoQiQ1fEB7OQaXHIcJNRfL6UMs2d+PHJOpi6KcP4UDmov+nqD16zHD5DRh1mK7v02Owzw/jQsiOPJZWa/IMQAAUK94N57RHS0xdUlB/9PkGFyesZSXeqYPs2R/P3JMnebM9NxPmHXJ8IE/Fv2rBK0n9DyJ5G3dyppg97fJefHkvNmRBuHLhg98XI4BAIB6RW48TckNXpgl+9vkONqVFnumD7Nkfz9yTH8cG93bqqZ8+lcJWk+W63AT7RG1d+UYXHJemNAZZSjXdbUcAwAA9YrceMZLvefc/HbkEM9ldgUd1fjliEGe62R/mxzLPdMmeO4zzJL9/cgx/Vw/Jnk/djUvmqjumjwmMICYy68Jfutvi0//KkGr+YzJcppQ68mdwbNFzotrU4TOC9IMg0HzyZTsDwBAvSM3nrdMGVN1YzekjzquoJ+zQbxI1/l6A3peciPaWP+MDe2r/jhqqHO5e5k7bcmqFfsUtM4b5t34VtzP4I/Vr/WG/vky7xG4dxd9og4YPtBzuSzZ348cU6oAYebB63Nmqo27d6tz9e+nJt/iO2tYP3VoQV9nXlw9fkSKc+AGjvfpXyVoXa+nl9NNWvlFysDilhnPlr17nN876xD7V5+gJPvb5Lz4SUDofGHmNHWbHue39GOW18kauGShZxlxS/YHAKDekRtPNzC5lTu/zAlWuQvL1bSvvlTLtnytVm7f5gQw4xIdskYtW6o+27xJnafDzYbdu9SdeiMbG9LbqZpsPO1xmHOR5FjsmrJiufrnxNHqxfLZ6jAd9iq+FkD37L5kgTpYj+XE1Bv6EbK/H3tM1Z2/9mNdx+qeJmjdrufBwnVrnfm0YccOtW7nDnW2DjqLv97sma6iRgw806d/laD14+HecDNk6SKnj3nsR+l5YX6a8BIb2kedPSwR9sxlp+j+m/XYzN9rt231DTiyv00uK0Ghc/327ToI91Ztp092vvrhqZIiJ5Cfq5+Ty3U4++9c8yGHxLTTv1rhmd6Uns8jZX8AAOqdVOHmIr0xvK9oomqsN5BlG9c7YeZTHbQWrl+rCnS4MqHDbMzNEa33Ppmj+uhQtlIHiQ8XzlOLdfCSG09dE2V/W5VQo8fiFwRMmeBnvlfrRh20ntO3fa50uhP6cnTf2KBe6kMdtHosXuAc9ZLTWtVO9vcjx+RzP04dpOfD8mSIMkHroyULnf736cBlws3UlV84f5v5JaetqCF9vu3Tv0rQkuEme1aRM5++1mHun7pX2eqvnD7L9fP02IwpavW2beqVmdOc+fKvccOdsVw1crA63eeE+kuGD/iv7G+rMi8CQucxuo4YakJfonbo58WELjOWDTpsvjN7hhP6WhRNUDdMGKV+FBDWLh0x6ALZHwCAesfeeLYtLa6y8exePtt5u9D8/veJo1SbmVNVz08Xqyv0hrpRQV819Itl6mT98yfDB6k/6o1442H9VOGXn6vfjhmmYskjKVVq+IBfyf42eyy36iDlmb4wcU7PHB0mzO836aD1kh7j0i2b1R69Qe86fbIOHtOcI1oxHRJnrFrpGwZMyd5B7DHFS4JPzm8xbYLzdqH5/YzkF2/+ZOQQdeTQvip34Sc64OxSXebM8kxX3ZjsoGXCTZVpdADup8Ol+d08F4W6ZuvHPFXPn1fmzXHC5449e9RtE0aq3p8tURfo22/Rfy/duMHTO1kp//F21aDlfcvW1MLNG52f5i3k9Tt3qvW7dqqD9Tx4bPoUtXLbVidord6xXZ2kr5/w5XLP9G6dP3Io/2AaAFD/2RvP+8TJ50EhpbYViw2Q7auwx3Kdz7lIpswRkI56o21+NyHQjPESHWi+r8ONOdpz66Qx6iIdKEzQuVaHPzl95VjSY4/p/qKJnvuprkzoGrdqhRqlA+gPg47eJEv2NuygZY442rc3R6bM/TvT6mB7hA6X5WtWqcYjBifeOhzSR52TvP6C5AcaDtZ/XxxwbtXF44YeKPvb7Hnx+Fz/0Pgj69y4M3WvHyb7m+fKfPP7+zpsmnGZ5+08n+ndkr0BAKiX7I3nb8YUeDZ4YZbsLdljcU+4j6jWyt5B7DEFvs0VTm2TvQ07aHmOaPnUAUNTnpeWsmRvyZ4XN0wa5Zk+nUr3y15lbwAA6qWq4cbn7b7QamCp7C1VBoqS0I+mVa2B18jeQfR4VrvjSjck1LJ6yN6G7jvZ7f+70UPlNKGW7C3Zy8rPAo6KhVRbZW8AAOolvdHs4m48o/wizEuGD/yZ7C3ZQUtOH3JdKHsH6dq37wEVQSv5SbkoSvZ16b6t3P6/rOb7zPa1ZG+pW3nJqMp54Z0+rLpsWH/P11wAAFBvdZk98yB5/k+Ydcmw/tWGLKNrWclVZiP+ZIRjuTTgLbrqPDlv9pV62r+EXZelEfr0PJll5ov8xGGYJXsG0ePYG+X/oLxs+IA7ZE8AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABCdg+UFAb4tLxAOSv78rs9l37Iuq853rN/d6f1UNx4/9n0Hqc39AgAAeLwo/j4m+fMAXSfoOlHXUbpO13Wrru/pujZ5GxOe7tL1++TfxiHJn2baJ63L39d1rPV3tq6jk78fpuuIWOL+TLC6272R5WxdR4rL/hBLjO9QXacmfzdMb+n45E/T6yf2FUkmgH0/+fsD1mXpBDMAAABfLyd/muDTUdcHut7Q1UlXbvK6l5I/TdAyfpv8+btYItTcm/z7zeTPS2KJQHOcrv8kL3tB18JYInD10xWPJfooXb2TtzkplghMg5J/ux7U9WNd7+i6U9dkXQN0/W/y+meSPxcl6zJdq3Wt1NVX10fJ6w1ztO3hWCIstoklQtXJun6YvP615GVvxxKP/+nk5QAAADVmjlyZ4GLeLjNHkky4MAHE9i9d/XVdKS43/mH9Pj6WOKo0Ifm3ue8pyd/vSf40cnRdaP1tjIgljqYdruv/dP0sefnE5M+pyZ9/jiUC32mxRKAzY++qa4yud2OJwGiOfpkjcE1iibE/qutDM7FWkPxpjsyZx2vG2CN52cDkT3OEzoRIE/BMXR/j7UQAABAieU4VQQMAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACV/h8ReJxKUASxXgAAAABJRU5ErkJggg==>
