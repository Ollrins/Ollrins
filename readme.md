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
  <em>Рисунок 3 - Подключение к контейнеру и остановка через Ctrl+C</em>
</p>

<p align="center">
  <img src="screenshots/task3-ps-a.png" alt="Статус контейнера" width="700"/>
  <br>
  <em>Рисунок 4 - Контейнер остановлен после Ctrl+C</em>
</p>

<p align="center">
  <img src="screenshots/task3-edit-config.png" alt="Редактирование конфига" width="850"/>
  <br>
  <em>Рисунок 5 - Изменение порта с 80 на 81 через nano</em>
</p>

<p align="center">
  <img src="screenshots/task3-curl-inside.png" alt="Проверка внутри контейнера" width="750"/>
  <br>
  <em>Рисунок 6 - Проверка curl внутри контейнера (80 не работает, 81 работает)</em>
</p>

<p align="center">
  <img src="screenshots/task3-curl-host.png" alt="Проверка с хоста" width="700"/>
  <br>
  <em>Рисунок 7 - Проверка с хостовой машины (не работает)</em>
</p>

<p align="center">
  <img src="screenshots/task3-rm-f.png" alt="Принудительное удаление" width="650"/>
  <br>
  <em>Рисунок 8 - Удаление работающего контейнера через docker rm -f</em>
</p>

## Задание 4: Общая папка между контейнерами

<p align="center">
  <img src="screenshots/task4-create-dir.png" alt="Создание директории" width="700"/>
  <br>
  <em>Рисунок 9 - Создание рабочей директории</em>
</p>

<p align="center">
  <img src="screenshots/task4-run-centos.png" alt="Запуск CentOS" width="800"/>
  <br>
  <em>Рисунок 10 - Запуск контейнера CentOS с volume</em>
</p>

<p align="center">
  <img src="screenshots/task4-run-debian.png" alt="Запуск Debian" width="800"/>
  <br>
  <em>Рисунок 11 - Запуск контейнера Debian с volume</em>
</p>

<p align="center">
  <img src="screenshots/task4-create-from-centos.png" alt="Создание файла из CentOS" width="750"/>
  <br>
  <em>Рисунок 12 - Создание файла из контейнера CentOS</em>
</p>

<p align="center">
  <img src="screenshots/task4-create-from-host.png" alt="Создание файла с хоста" width="650"/>
  <br>
  <em>Рисунок 13 - Создание файла на хостовой машине</em>
</p>

<p align="center">
  <img src="screenshots/task4-check-from-debian.png" alt="Проверка из Debian" width="750"/>
  <br>
  <em>Рисунок 14 - Проверка файлов из контейнера Debian</em>
</p>

## Задание 5: Portainer и локальный registry

<p align="center">
  <img src="screenshots/task5-create-files.png" alt="Создание файлов" width="800"/>
  <br>
  <em>Рисунок 15 - Создание compose.yaml и docker-compose.yaml</em>
</p>

<p align="center">
  <img src="screenshots/task5-first-up.png" alt="Первый запуск" width="750"/>
  <br>
  <em>Рисунок 16 - Запуск docker compose up -d (только portainer)</em>
</p>

<p align="center">
  <img src="screenshots/task5-include.png" alt="Include в compose" width="700"/>
  <br>
  <em>Рисунок 17 - Добавление include в compose.yaml</em>
</p>

<p align="center">
  <img src="screenshots/task5-both-running.png" alt="Оба сервиса" width="800"/>
  <br>
  <em>Рисунок 18 - Оба контейнера (portainer и registry) запущены</em>
</p>

<p align="center">
  <img src="screenshots/task5-push-to-registry.png" alt="Push в registry" width="850"/>
  <br>
  <em>Рисунок 19 - Загрузка образа в локальный registry</em>
</p>

<p align="center">
  <img src="screenshots/task5-portainer-login.png" alt="Portainer login" width="700"/>
  <br>
  <em>Рисунок 20 - Начальная настройка Portainer</em>
</p>

<p align="center">
  <img src="screenshots/task5-portainer-stack.png" alt="Stack в Portainer" width="900"/>
  <br>
  <em>Рисунок 21 - Деплой стека через Portainer web editor</em>
</p>

<p align="center">
  <img src="screenshots/task5-portainer-inspect.png" alt="Inspect в Portainer" width="1000"/>
  <br>
  <em>Рисунок 22 - Просмотр Config контейнера (AppArmorProfile до Driver)</em>
</p>

<p align="center">
  <img src="screenshots/task5-warning.png" alt="Warning" width="800"/>
  <br>
  <em>Рисунок 23 - Предупреждение об отсутствующем файле</em>
</p>

<p align="center">
  <img src="screenshots/task5-down.png" alt="Остановка проекта" width="600"/>
  <br>
  <em>Рисунок 24 - Остановка проекта одной командой docker compose down</em>
</p>

## Итоговый compose.yaml

```yaml
version: "3"
services:
  portainer:
    network_mode: host
    image: portainer/portainer-ce:latest
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock