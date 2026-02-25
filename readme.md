# Домашнее задание по Docker

## Задание 1: hub.docker.com 

<p align="center">
  <br>
  <em>https://hub.docker.com/r/ollrins/custom-nginx</em>
</p>

## Задание 2: Запуск custom-nginx

<p align="center">
  <img src="screenshots/task2-docker-ps.png" alt="Выполнение команд задания 2" width="900"/>
  <br>
  <em>Рисунок 1 - Запуск контейнера, переименование и проверка. Доступность страницы через curl</em>
</p>



## Задание 3: Изменение конфигурации nginx

<p align="center">
  <img src="screenshots/task3-attach.png" alt="docker attach" width="800"/>
  <br>
  <em>Рисунок 2 - Подключение к контейнеру и остановка через Ctrl+C</em>
  <em>Контейнер остановился, потому что мы послали сигнал остановки главному процессу (nginx), который был запущен как PID 1. Когда процесс PID 1 завершается, контейнер останавливается.</em>
</p>

<p align="center">
  <img src="screenshots/task3-edit-config.png" alt="Редактирование конфига" width="850"/>
  <br>
  <em>Рисунок 3 - Изменение порта с 80 на 81 через nano</em>
  
</p>

<p align="center">
  <img src="screenshots/task3-curl-inside.png" alt="Проверка внутри контейнера. Проверка с хоста" width="750"/>
   <img src="screenshots/task3-edit-config2.png alt="Проверка внутри контейнера. Проверка с хоста" width="750"/>
  <br>
  <em>Рисунок 4 - Проверка curl внутри контейнера (80 не работает, 81 работает). Проверка с хостовой машины (не работает)</em>
  <em>Проблема: curl 80 не работает, Nginx внутри слушает порт 81, но Docker при запуске контейнера пробросил хост-порт 8080 на контейнер-порт 80 (так было в команде run). Теперь внутри контейнера порт 80 не слушается, поэтому внешний запрос падает в пустоту.</em>
</p>

<p align="center">
  <img src="screenshots/task3-curl-host.png" alt="Дополнительное задание" width="700"/>
  <br>
  <em>Рисунок 5 - Дополнительное задание</em>
</p>


## Задание 4: Общая папка между контейнерами

<p align="center">
  <img src="screenshots/task4-create-dir.png" alt="Общая папка между контейнерами" width="700"/>
  <br>
  <em>Рисунок 6 - Создание рабочей директории. Запуск контейнера CentOS с volume. Запуск контейнера Debian с volume. Создание файла из контейнера CentOS. Создание файла на хостовой машине. Проверка файлов из контейнера Debian </em>
</p>

<p align="center">
  <br>
  <em>Будет пояснение</em>
</p>



## Задание 5: Portainer и локальный registry

<p align="center">
  <img src="screenshots/task5-create-files.png" alt="Создание файлов" width="800"/>
  <br>
  <em>Рисунок 7 - Создание compose.yaml и docker-compose.yaml. Запуск docker compose up -d (только portainer). Добавление include в compose.yaml. Оба контейнера (portainer и registry) запущены </em>
  <em> Был запущен compose.yaml, Docker Compose по умолчанию ищет файлы в порядке приоритета: compose.yaml (предпочтительнее), затем compose.yml, затем docker-compose.yaml, рекомендуется использовать compose.yaml как стандартное имя</em>
</p>

<p align="center">
  <img src="screenshots/task5-compose.png" alt="Stack в Portainer" width="900"/>
  <br>
  <em>Рисунок 8 - compose.yaml</em>
</p>

<p align="center">
  <img src="screenshots/task5-push-to-registry.png" alt="Push в registry" width="850"/>
   <img src="screenshots/task5-push.png" alt="Push в registry" width="850"/>
  <br>
  <em>Рисунок 9 - Загрузка образа в локальный registry</em>
</p>



<p align="center">
  <img src="screenshots/task5-portainer-inspect.png" alt="Inspect в Portainer" width="1000"/>
  <br>
  <em>Рисунок 10 - Просмотр Config контейнера (AppArmorProfile до Driver)</em>
</p>

<p align="center">
  <img src="screenshots/task5-warning.png" alt="Warning" width="800"/>
  <br>
  <em>Рисунок 11 - Предупреждение об отсутствующем файле. Остановка проекта одной командой docker compose down</em>
  <em>В compose.yaml есть директива include, которая ссылается на несуществующий файл docker-compose.yaml. Docker Compose предупреждает, что этот файл не найден и будет проигнорирован.</em>
</p>


