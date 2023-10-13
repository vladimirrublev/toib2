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
1 Шаг ![image](https://github.com/vladimirrublev/toib2/blob/main/1%20часть.PNG)

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

![image](https://github.com/asatryan173/TOIB2/assets/71139053/37f49d43-85ef-41a6-a502-7c5357a5ad3a)

4 Шаг

root@debian:/home/volodyarvs# sudo usermod -aG group-{rublev} super-{Rublev.V.S}

![image](https://github.com/asatryan173/TOIB2/assets/71139053/43c5b913-d064-457a-8f4c-475a8c5b1198)

5 Шаг

root@debian:/home/volodyarvs# id super-{Rublev.V.S}

uid=1002(super-{Rublev.V.S}) gid=1002(super-{Rublev.V.S}) группы=1002(super-{Rublev.V.S
}),27(sudo), 1003(group-{rublev})

![image](https://github.com/asatryan173/TOIB2/assets/71139053/b0798775-00cf-48c2-a40e-d6ca12163a2d)

6 Шаг

root@debian:/home/volodyarvs# sudo adduser user_vladimir

root@debian:/home/volodyarvs# sudo usermod -aG group-{rublev} user_vladimir

root@debian:/home/volodyarvs# id user_vladimir

uid=1004(user_vladimir) gid=1004(user_vladimir) группы=1004(user_vladimir),100(users),1003(group
-{Rublev.V.S})

![image](https://github.com/asatryan173/TOIB2/assets/71139053/b109c18c-a714-4baa-83c2-3978ee915c0f)

![image](https://github.com/asatryan173/TOIB2/assets/71139053/b0d9d7e0-b595-4d76-aee2-5f0c0ef7d915)

7 Шаг

root@debian:/home/volodyarvs# sudo mkdir /home/super-{Rublev.V.S}

root@debian:/home/volodyarvs# chmod 770 /home/super-{Rublev.V.S}

root@debian:/home/volodyarvs# chown super-{Rublev.V.S}:group-{rublev} /home/super-{Rublev.V.S}

![image](https://github.com/asatryan173/TOIB2/assets/71139053/fc3ba5de-fdc7-46db-984d-56372d906fa3)

8 Шаг

root@debian:/home/volodyarvs# su user_volodyarvs

user_volodyarvs@debian:/home/volodyarvs$ touch /home/super-{Rublev.V.S}/test_file.txt

user_volodyarvs@debian:/home/volodyarvs$ rm /home/super-{Rublev.V.S}/test_file.txt

![image](https://github.com/asatryan173/TOIB2/assets/71139053/4c75eb4d-e436-4dea-b394-a24a5614d17a)

user_volodyarvsr@debian:/home/volodyarvs$ cd /home/super-{Rublev.V.S}

user_volodyarvs@debian:/home/super-{[Rublev.V.S](https://media.discordapp.net/attachments/1162377161605386250/1162380594433511504/image.png?ex=653bba49&is=65294549&hm=e5ff9cb3a64f1c124f80852ab32ad4bf7852d42b05972cfec8f55e1b1a2b0dce&=)}$ touch test_file.txt

user_volodyarvs@debian:/home/super-{Rublev.V.S}$ ls

test_file.txt

![image](https://github.com/asatryan173/TOIB2/assets/71139053/07967d72-5356-4b87-9888-45af2fc6c89c)
