# donasktello_microservices
## Д/3 №11
- Репозиторий настроен на интеграцию с travis-ci
- Установлен Docker
- Запущен первый контейнер 'Hello, world'
- Создан и закоммитен первый образ на основе запущенного контейнера

## Д/3 №12
- Создал GCP проект docker
- Создан инстанс docker-host через docker-machine
- Собран билд реддит проекта на докер хост
- Контейнер запущен на докер хосте и прописано правило файрвола для доступа
- Образ билда запушен на докер хаб
- Контейнер из образа запущен и проверен локально

## Д/З №13
- Скачан и распакован архив microservices
- Поочерёдно созданы Dockerfile для каждого из 3 микросервисов(комменты, посты и ui)
- Сбилдены образы для всех 3 микросервисов
- Создана сеть для приложения
- Микросервисы соединены в одну общую сеть
- Создан volume для mongo_db и подключен при запуске контейнера монго

## Д/З №14
- Поработали с none сетевым драйвером на примере тестового контейнера
- Поработали с host сетевым драйвером на примере тестового контейнера
- Поработали с bridge сетевым драйвером на примере тестового контейнера
- Запустили реддит проект в 2 бридж сетях
- Посмотрели на конфигурацию iptables на docker-host
- Переписали проект под использование docker-compose
    ###Как образуется базовое имя проекта?
    Указать -p, --project-name NAME

## Д/З №15
- Создали виртуальную машину для gitlab-ci
- Установили докер на вм gitlab-ci
- Развернули gitlab-ci через docker-compose
- Создали рабочую группу и проект
- Добавили remote для заливки проекта
- Создали и настроили .gitlab-ci.yml
- Запустили контейнер для runner, указав креды доступа с нашего проекта
- Проставили галочку для запуска tagged jobs в настройках runner
- Залили reddit проект в репозиторий и изменили .gitlab-ci.yml для теста reddit
- Добавили файл simpletest для теста reddit и добавили гем rack-test для тестов

## Д/3 №16
- Создали новый проект example2 в gitlab-ci контейнере
- Добавили в качестве git репозитория gitlab2
- Расшарили runner на оба проекта, поменяв при этом .toml файл указав новый эфемерный ip
- Добавили dev environment
- Определили stage и prod окружения с ограничением по ручному деплою
- Сделали условие на наличие тега для деплоя на stage и prod окружения
- Создали возможность динамического окружения

## Д/3 №17
- Создали правила firewall для Prometheus и Puma (--allow tcp:9090 --allow tcp:9292)
- Создадим Docker хост в GCE и настроим локальное окружение на работу с ним
- Запускаем Prometheus из готового контейнера
- Переогранизовали предыдущую структуру и перенесли все докер файлы в единую docker директорию
- Копируем конфигурацию из готового контейнера Prometheus в наш контейнер
- Определяем конфигурационный файл для сбора метрик с наших микросервисов
- Билдим образ Prometheus контейнера на итоге собранных данных
- Сбилдили все образы наших микросервисов
- Отрефакторили docker-compose.yml(Убрали билд и актуализировали обращение к image, дописали контейнер Prometheus)
- Проверили docker-compose микросервисов в связке с Prometheus
- Остановили работу одного из микросервисов и убедились в том, что healthchecks возвращают down состояние микросервиса
- Познакомились с Exporters(Программа, которая делает метрики доступными для сбора Prometheus. Используется когда нельзя поменять код
    приложения. Примеры: PostgreSQL, RabbitMQ, Nginx, Node exporter, cAdvisor)
- Воспользовались Node экспортер и заодно допишем его в наш docker-compose. Также добавили в конфигурацию Prometheus ещё один 
    ендпойнт для сбора метрик(node-exporter:9100)
- Пересобрали образ Prometheus с новой конфигурацией и пересобрали наш docker-compose
- Запушили все наши образы микросервисов, Prometheus на DockerHub