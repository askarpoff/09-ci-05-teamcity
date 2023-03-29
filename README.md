# Домашнее задание к занятию 11 «Teamcity»

## Подготовка к выполнению

1. В Yandex Cloud создайте новый инстанс (4CPU4RAM) на основе образа `jetbrains/teamcity-server`.
2. Дождитесь запуска teamcity, выполните первоначальную настройку.
3. Создайте ещё один инстанс (2CPU4RAM) на основе образа `jetbrains/teamcity-agent`. Пропишите к нему переменную окружения `SERVER_URL: "http://<teamcity_url>:8111"`.
4. Авторизуйте агент.
5. Сделайте fork [репозитория](https://github.com/aragastmatb/example-teamcity).
6. Создайте VM (2CPU4RAM) и запустите playbook
![image](https://user-images.githubusercontent.com/108946489/228396420-e9827bba-40d5-4754-8b37-29f1ca06226a.png)

## Основная часть

1. Создайте новый проект в teamcity на основе fork.
2. Сделайте autodetect конфигурации.
![image](https://user-images.githubusercontent.com/108946489/228397918-786c7230-9e26-4729-a9da-68b3e6a2908c.png)
3. Сохраните необходимые шаги, запустите первую сборку master.
![image](https://user-images.githubusercontent.com/108946489/228400704-264e6368-6a7b-4126-8334-cdaa35506644.png)
4. Поменяйте условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`.
![image](https://user-images.githubusercontent.com/108946489/228402884-9c1b421b-18be-4aa5-98c2-3136d59913c0.png)
5. Для deploy будет необходимо загрузить settings.xml в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.
![image](https://user-images.githubusercontent.com/108946489/228404551-c42d8d6d-9606-4295-bf79-5d956378b090.png)
6. В pom.xml необходимо поменять ссылки на репозиторий и nexus.
![image](https://user-images.githubusercontent.com/108946489/228404835-453c1eb9-986a-47b0-b24b-1f4dab7ef7ab.png)
7. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.
![image](https://user-images.githubusercontent.com/108946489/228407747-ee5f63d6-ed98-4d2b-9b69-c0739ce4e701.png)
8. Мигрируйте `build configuration` в репозиторий.
![image](https://user-images.githubusercontent.com/108946489/228449194-c4c08ee1-8f98-427b-a621-77ee73764f99.png)
9. Создайте отдельную ветку `feature/add_reply` в репозитории.
10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`.
11. Дополните тест для нового метода на поиск слова `hunter` в новой реплике.
12. Сделайте push всех изменений в новую ветку репозитория.
13. Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.
![image](https://user-images.githubusercontent.com/108946489/228452407-c21463ad-bec9-4071-9976-c344bda32787.png)
14. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`.
15. Убедитесь, что нет собранного артефакта в сборке по ветке `master`.
![image](https://user-images.githubusercontent.com/108946489/228457960-91be2e50-e672-42a0-af9a-6834be83d048.png)
16. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.
![image](https://user-images.githubusercontent.com/108946489/228458193-7cffddcc-5990-47cc-8fe7-bb87111145e6.png)
17. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.
![image](https://user-images.githubusercontent.com/108946489/228457540-40f47f0a-76d2-4d8a-bfef-121d31dc5f5e.png)
18. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.
![image](https://user-images.githubusercontent.com/108946489/228458460-3aea90a4-dfc6-4a85-b0ac-9521eb823a5a.png)
19. В ответе пришлите ссылку на репозиторий.
<a href='https://github.com/askarpoff/example-teamcity'>https://github.com/askarpoff/example-teamcity</a>
---
