# Домашнее задание к занятию «Teamcity»

## Подготовка к выполнению

1. В Yandex Cloud создана необходимая инфраструктурв:    
     
![](https://github.com/OlgaLesnykh/screenshots/blob/main/Teamcity_001.png)    

2. Выполнена первоначальная настройка teamcity-server, авторизован агент:    
    
![](https://github.com/OlgaLesnykh/screenshots/blob/main/Teamcity_003.png)    

5. Выполнен fork репозитория example-teamcity.
6. Успешно выполнен playbook для ВМ nexus.    
    
![](https://github.com/OlgaLesnykh/screenshots/blob/main/Teamcity_002.png)    

## Основная часть

1. Создайте новый проект в teamcity на основе fork.
2. Сделайте autodetect конфигурации.
3. Сохраните необходимые шаги, запустите первую сборку master.    
    
![](https://github.com/OlgaLesnykh/screenshots/blob/main/Teamcity_004.png)    
    
4. Поменяйте условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`. (у меня в названии ветки main вместо master, суть не меняется):    
    
![](https://github.com/OlgaLesnykh/screenshots/blob/main/Teamcity_006.png)   
     
5. Для deploy будет необходимо загрузить [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.
6. В pom.xml необходимо поменять ссылки на репозиторий и nexus.
7. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.    
    
![](https://github.com/OlgaLesnykh/screenshots/blob/main/Teamcity_005.png)    
    
8. Мигрируйте `build configuration` в репозиторий.    
    
![](https://github.com/OlgaLesnykh/screenshots/blob/main/Teamcity_007.png)    
    
9. Создайте отдельную ветку `feature/add_reply` в репозитории.
10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`.
11. Дополните тест для нового метода на поиск слова `hunter` в новой реплике.
12. Сделайте push всех изменений в новую ветку репозитория.
13. Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.    
    
![](https://github.com/OlgaLesnykh/screenshots/blob/main/Teamcity_008.png)    
    
14. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`.
15. Убедитесь, что нет собранного артефакта в сборке по ветке `master`.    
    
![](https://github.com/OlgaLesnykh/screenshots/blob/main/Teamcity_009.png)    
    
16. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.    
    
![](https://github.com/OlgaLesnykh/screenshots/blob/main/Teamcity_010.png)    
    
17. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.    
    
![](https://github.com/OlgaLesnykh/screenshots/blob/main/Teamcity_011.png)    
    
18. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.
19. В ответе пришлите ссылку на репозиторий.
