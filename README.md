# example-playbook

Jenkins это нечто. Более капризный тул ещё надо поискать. За красивой внешностью прячутся такие сложности. Вряд ли я когда-нидубь буду его использовать 
после всего того, что удалось пережить во время выполнения этого домашнего задания.

Настройка соединения с github вылилась в целую эпопею. Которая в конце концов решилась с помощью Credential - "SSH Username with private key". 
Только с его помощью удалось победить конструкцию 
git credentialsId: 'cb0b173c-2e3b-466f-b570-cacc58d05021', url: 'git@github.com:aragastmatb/example-playbook.git'

1. Поскольку я использовал Jenkins в контейнере, пришлось настраивать docker на хосте чтобы он слушал порт 2375.
После этого удалось создать docker ноду в http://192.168.1.193:8080/configureClouds/

2. Создал контейнер, пользуясь /09-ci-03-jenkins/docker/Dockerfile На этом этапе очень удивилсял зачем нужны иксы и десятки сопуствующих 
библиотек в контейнере. 

3. Следующая проблема настигла вот тут:
```
withCredentials([usernamePassword(credentialsId: 'a0f1679b-ac18-40c0-bfb8-7cbd55f74abb', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')])
```
Окзалаось что withCredentials не работает в консоли Jenkins. И после этого всё наконец-то заработало. Чего и всем желаю.




