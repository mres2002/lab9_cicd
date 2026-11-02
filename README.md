DevOps Lab 13: CI/CD Pipeline
Описание
Репозиторий содержит пример приложения на Python с настроенным полным циклом CI/CD/GitOps.

Структура проекта
devops13cicd/ ├── .github/workflows/ │ ├── cicd.yml # CI пайплайн (lint, test, build) │ └── release.yml # CD пайплайн (build, push) ├── server/ │ ├── application.py # Исходный код приложения │ ├── test_application.py # Юнит-тесты │ └── dockerfile # Docker образ ├── server-k8s-manifests/ │ └── devops-psu.yml # Kubernetes манифесты ├── screenshots/ # Скриншоты выполнения ├── requirements.txt # Python зависимости └── README.md # Этот файл

Как это работает
CI (Continuous Integration)
Разработчик пушит код в ветку dev
GitHub Actions запускает проверки:
lint — проверка кода через pylint
unit-tests — запуск pytest
build-test — сборка и тест Docker образа
CD (Continuous Delivery)
После мержа в master запускается release пайплайн
Образ собирается и пушится в Docker Hub
Манифест обновляется и пушится в ветку release
GitOps (ArgoCD)
ArgoCD отслеживает ветку release
При изменениях автоматически синхронизирует кластер
Приложение обновляется без участия человека
Скриншоты
Все скриншоты успешного выполнения находятся в папке screenshots/
