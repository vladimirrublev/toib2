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
1 Шаг ![image](https://github.com/asatryan173/TOIB2/assets/71139053/bbd358ee-d20d-484d-943b-314fdf69ef94)

2 Шаг

david@debian:~$ su

Пароль: 

root@debian:/home/david# sudo useradd super-{AsatryanDR}

root@debian:/home/david# passwd super-{AsatryanDR}

Новый пароль:

Повторите ввод нового пароля: 

passwd: пароль успешно обновлён

root@debian:/home/david# sudo usermod -aG sudo super-{AsatryanDR}

![image](https://github.com/asatryan173/TOIB2/assets/71139053/2492927f-9e97-4ccf-a9b9-e068ee2a28f2)

3 Шаг

root@debian:/home/david# sudo groupadd group-{1234}

![image](https://github.com/asatryan173/TOIB2/assets/71139053/37f49d43-85ef-41a6-a502-7c5357a5ad3a)

4 Шаг

root@debian:/home/david# sudo usermod -aG group-{1234} super-{AsatryanDR}

![image](https://github.com/asatryan173/TOIB2/assets/71139053/43c5b913-d064-457a-8f4c-475a8c5b1198)

5 Шаг

root@debian:/home/david# id super-{AsatryanDR}

uid=1002(super-{AsatryanDR}) gid=1002(super-{AsatryanDR}) группы=1002(super-{AsatryanDR
}),27(sudo), 1003(group-{1234})

![image](https://github.com/asatryan173/TOIB2/assets/71139053/b0798775-00cf-48c2-a40e-d6ca12163a2d)

6 Шаг

root@debian:/home/david# sudo adduser user_david

root@debian:/home/david# sudo usermod -aG group-{1234} user_david

root@debian:/home/david# id user_david

uid=1004(user_david) gid=1004(user_david) группы=1004(user_david),100(users),1003(group
-{1234})

![image](https://github.com/asatryan173/TOIB2/assets/71139053/b109c18c-a714-4baa-83c2-3978ee915c0f)

![image](https://github.com/asatryan173/TOIB2/assets/71139053/b0d9d7e0-b595-4d76-aee2-5f0c0ef7d915)

7 Шаг

root@debian:/home/david# sudo mkdir /home/super-{AsatryanDR}

root@debian:/home/david# chmod 770 /home/super-{AsatryanDR}

root@debian:/home/david# chown super-{AsatryanDR}:group-{1234} /home/super-{AsatryanDR}

![image](https://github.com/asatryan173/TOIB2/assets/71139053/fc3ba5de-fdc7-46db-984d-56372d906fa3)

8 Шаг

root@debian:/home/david# su user_david

user_david@debian:/home/david$ touch /home/super-{AsatryanDR}/test_file.txt

user_david@debian:/home/david$ rm /home/super-{AsatryanDR}/test_file.txt

![image](https://github.com/asatryan173/TOIB2/assets/71139053/4c75eb4d-e436-4dea-b394-a24a5614d17a)

user_david@debian:/home/david$ cd /home/super-{AsatryanDR}

user_david@debian:/home/super-{AsatryanDR}$ touch test_file.txt

user_david@debian:/home/super-{AsatryanDR}$ ls

test_file.txt

![image](https://github.com/asatryan173/TOIB2/assets/71139053/07967d72-5356-4b87-9888-45af2fc6c89c)
