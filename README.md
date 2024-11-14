# «Сетевое взаимодействие в K8S. Часть 1»-Абрамов Сергей

### Цель задания

В тестовой среде Kubernetes необходимо обеспечить доступ к приложению, установленному в предыдущем ДЗ и состоящему из двух контейнеров, по разным портам в разные контейнеры как внутри кластера, так и снаружи.

------

### Чеклист готовности к домашнему заданию

1. Установленное k8s-решение (например, MicroK8S).
2. Установленный локальный kubectl.
3. Редактор YAML-файлов с подключённым Git-репозиторием.

------

### Инструменты и дополнительные материалы, которые пригодятся для выполнения задания

1. [Описание](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) Deployment и примеры манифестов.
2. [Описание](https://kubernetes.io/docs/concepts/services-networking/service/) Описание Service.
3. [Описание](https://github.com/wbitt/Network-MultiTool) Multitool.

------

### Задание 1. Создать Deployment и обеспечить доступ к контейнерам приложения по разным портам из другого Pod внутри кластера

1. Создать Deployment приложения, состоящего из двух контейнеров (nginx и multitool), с количеством реплик 3 шт.

Пространство имен для выполнения задания:

![k1](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/png/k1.png)

[deployment.yaml](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/pod_yaml/deployment.yaml)

![k2](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/png/k2.png)

2. Создать Service, который обеспечит доступ внутри кластера до контейнеров приложения из п.1 по порту 9001 — nginx 80, по 9002 — multitool 8080.

[svc_n_m.yaml](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/pod_yaml/svc_n_m.yaml)

![k3](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/png/k3.png)

3. Создать отдельный Pod с приложением multitool и убедиться с помощью `curl`, что из пода есть доступ до приложения из п.1 по разным портам в разные контейнеры.

[multitool.yaml](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/pod_yaml/multitool.yaml)

![k4](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/png/k4.png)

4. Продемонстрировать доступ с помощью `curl` по доменному имени сервиса.

![k9](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/png/k9.png)

5. Предоставить манифесты Deployment и Service в решении, а также скриншоты или вывод команды п.4.

![k5](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/png/k5.png)

![k6](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/png/k6.png)

![k7](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/png/k7.png)

![k8](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/png/k8.png)

------

### Задание 2. Создать Service и обеспечить доступ к приложениям снаружи кластера

1. Создать отдельный Service приложения из Задания 1 с возможностью доступа снаружи кластера к nginx, используя тип NodePort.

[svc_nodeport.yaml](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/pod_yaml/svc_nodeport.yaml)

![k10](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/png/k10.png)

2. Продемонстрировать доступ с помощью браузера или `curl` с локального компьютера.

![k11](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/png/k11.png)

3. Предоставить манифест и Service в решении, а также скриншоты или вывод команды п.2.

![k12](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/png/k12.png)

![k13](https://github.com/smabramov/K8s-1-4/blob/3fc98bf9268c4e283b349b96d80f08526ce1add4/png/k13.png)
------

### Правила приёма работы

1. Домашняя работа оформляется в своем Git-репозитории в файле README.md. Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода необходимых команд `kubectl` и скриншоты результатов.
3. Репозиторий должен содержать тексты манифестов или ссылки на них в файле README.md.

