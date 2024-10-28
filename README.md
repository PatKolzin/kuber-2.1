# Домашнее задание к занятию "`Хранение в K8s. Часть 1`"



---

### Задание 1 


Создать Deployment приложения, состоящего из двух контейнеров и обменивающихся данными.

1. Создать Deployment приложения, состоящего из контейнеров busybox и multitool.
2. Сделать так, чтобы busybox писал каждые пять секунд в некий файл в общей директории.
3. Обеспечить возможность чтения файла контейнером multitool.
4. Продемонстрировать, что multitool может читать файл, который периодоически обновляется.
5. Предоставить манифесты Deployment в решении, а также скриншоты или вывод команды из п. 4.

Создадаю namespace для задания:

![image](https://github.com/user-attachments/assets/2898c39b-8515-4bbe-acd4-44fa967cab5d)


1. Пишу Deployment приложения, состоящего из контейнеров busybox и multitool.

2. Чтобы busybox записывал данные каждые пять секунд в соответствующий файл в общей директории, буду использовать команду создающую общую директорию и общий файл. Далее в созданный файл каждые пять секунд будет записываться текущее время и дата.

3. Для обеспечения чтения файла контейнером multitool, в манифесте Deployment укажу общую с контейнером busybox директорию, читать файл буду с помощью команды `tail`.

4. Проверяю, записались ли данные в файл контейнером busybox и будут ли они доступны контейнеру multitool.

![image](https://github.com/user-attachments/assets/72017152-c20f-491c-af6e-34bbb4a1ae43)
![image](https://github.com/user-attachments/assets/8d7e454f-ad0b-4e9a-9ce8-a350cd57822c)

Файл, созданный в контейнере Busybox доступен для чтения контейнером multitool

5. Ссылка - [Deployment](https://github.com/PatKolzin/kuber-2.1/blob/main/src/deployment.yaml)
------

### Задание 2


Создать DaemonSet приложения, которое может прочитать логи ноды.

1. Создать DaemonSet приложения, состоящего из multitool.
2. Обеспечить возможность чтения файла `/var/log/syslog` кластера MicroK8S.
3. Продемонстрировать возможность чтения файла изнутри пода.
4. Предоставить манифесты Deployment, а также скриншоты или вывод команды из п. 2.

1. Пишу манифест DaemonSet приложения, состоящего из multitool. Применяю манифест и проверяю DaemonSet и Pod и проверяю возможность чтения файла изнутри пода::

![image](https://github.com/user-attachments/assets/62811d10-2dee-4c1f-b8ce-923c47c04fff)

Видно, что в контейнере пода присутствует файл logdata, который примонтирован из машины - кластера MicroK8S.

4. Ссылка на манифест [DaemonSet](https://github.com/PatKolzin/kuber-2.1/blob/main/src/daemonset.yaml)


