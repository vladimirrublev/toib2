# toib2
# Отчет по зданию №2 "Идентификация и аутентификация"
Задача 
1. Создать виртуальную машину на базе ОС Debian 12 https://www.virtualbox.org/wiki/Downloads
https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-12.1.0-amd64-netinst.iso
2. Создать пользователя super-{ФИО}, наделить его привилегиями суперпользователя
3. Зайти под созданным пользователем и создать группу group-{группа}
4. Добавить пользователя super-{ФИО} в группу group-{группа}
5. Продемонстрировать наличие пользователя в группе
6. Создать пользователя user-{ФИО}, добавить его в группу group-{группа}
7. Наделить полномочиями (с использованием механизмов дискреционного управления
доступом chmod) пользователя user-{ФИО} по созданию и удалению файлов в домашнем
каталоге пользователя super-{ФИО}
8. Продемонстрировать работу механизмов разграничения доступа.
# Шаги выполнения 
1 Шаг ![image](https://github.com/vladimirrublev/toib2/blob/main/1111111111111111111111111111111111111111111111111111111111111111.PNG)

2 Шаг

volodyarvs@debian:~$ su

Пароль: 

root@debian:/home/volodyarvs# sudo useradd super-{Rublev.V.S}

root@debian:/home/volodyarvs# passwd super-{Rublev.V.S}

Новый пароль:

Повторите ввод нового пароля: 

passwd: пароль успешно обновлён

root@debian:/home/volodyarvs# sudo usermod -aG sudo super-{Rublev.V.S}

![image](https://github.com/vladimirrublev/toib2/blob/main/1%20часть.PNG)

3 Шаг

root@debian:/home/volodyarvs# sudo groupadd group-{rublev}

![image](https://github.com/vladimirrublev/toib2/blob/main/2%20часть.PNG)

4 Шаг

root@debian:/home/volodyarvs# sudo usermod -aG group-{rublev} super-{Rublev.V.S}

![image](https://github.com/vladimirrublev/toib2/blob/main/3%20часть.PNG)

5 Шаг

root@debian:/home/volodyarvs# id super-{Rublev.V.S}

uid=1002(super-{Rublev.V.S}) gid=1002(super-{Rublev.V.S}) группы=1002(super-{Rublev.V.S
}),27(sudo), 1003(group-{rublev})

![image](https://github.com/vladimirrublev/toib2/blob/main/4%20часть.PNG)

6 Шаг

root@debian:/home/volodyarvs# sudo adduser user_vladimir

root@debian:/home/volodyarvs# sudo usermod -aG group-{rublev} user_vladimir

root@debian:/home/volodyarvs# id user_vladimir

uid=1004(user_vladimir) gid=1004(user_vladimir) группы=1004(user_vladimir),100(users),1003(group
-{Rublev.V.S})

![image](https://github.com/vladimirrublev/toib2/blob/main/5%20часть.PNG)

![image](https://github.com/vladimirrublev/toib2/blob/main/6%20часть.PNG)

7 Шаг

root@debian:/home/volodyarvs# sudo mkdir /home/super-{Rublev.V.S}

root@debian:/home/volodyarvs# chmod 770 /home/super-{Rublev.V.S}

root@debian:/home/volodyarvs# chown super-{Rublev.V.S}:group-{rublev} /home/super-{Rublev.V.S}

![image](https://github.com/vladimirrublev/toib2/blob/main/7.png)

8 Шаг

root@debian:/home/volodyarvs# su user_volodyarvs

user_volodyarvs@debian:/home/volodyarvs$ touch /home/super-{Rublev.V.S}/test_file.txt

user_volodyarvs@debian:/home/volodyarvs$ rm /home/super-{Rublev.V.S}/test_file.txt

![image](https://github.com/vladimirrublev/toib2/blob/main/8.png)

user_volodyarvsr@debian:/home/volodyarvs$ cd /home/super-{Rublev.V.S}

user_volodyarvs@debian:/home/super-{[Rublev.V.S](https://media.discordapp.net/attachments/1162377161605386250/1162380594433511504/image.png?ex=653bba49&is=65294549&hm=e5ff9cb3a64f1c124f80852ab32ad4bf7852d42b05972cfec8f55e1b1a2b0dce&=)}$ touch test_file.txt

user_volodyarvs@debian:/home/super-{Rublev.V.S}$ ls

test_file.txt
