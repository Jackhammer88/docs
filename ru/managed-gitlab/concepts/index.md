# Взаимосвязь ресурсов в {{ mgl-name }}

[{{ GL }}](https://about.gitlab.com/) — это веб-инструмент жизненного цикла [DevOps](/blog/posts/2022/03/what-is-devops) с открытым исходным кодом. Он представляет собой систему управления репозиториями кода для [Git](https://git-scm.com/) с системой отслеживания ошибок, [CI/CD](/blog/posts/2022/10/ci-cd) пайплайном, собственной Wiki и другими функциями.

{{ mgl-name }} позволяет настроить развертывание приложений на [виртуальных машинах](../../compute/concepts/vm.md) [{{ compute-full-name }}](../../compute/), а также поддерживает интеграцию с [{{ container-registry-full-name }}](../../container-registry/) и [{{ managed-k8s-full-name }}](../../managed-kubernetes/).

Схема работы {{ mgl-name }}:

![image](../../_assets/managed-gitlab/gitlab_schema_ru.svg)

## Инстанс {{ GL }} {#instance}

_Инстанс_ {{ GL }} — основная сущность, которой оперирует сервис. Это ВМ, размещенная в {{ yandex-cloud }}. {{ mgl-name }} берет на себя рутинные операции по техническому обслуживанию этой ВМ, например, обеспечение отказоустойчивости хранилища, установку обновлений безопасности, автоматизированное обновление до новых версий {{ GL }} и т. д.

## Конфигурация инстанса {#config}

При создании инстанса указываются:
* Тип инстанса — [количество ядер (vCPU) и объем памяти (RAM)](../../compute/concepts/vm-platforms.md). После создания инстанса можно [изменить его тип](../operations/instance/instance-update.md) на более производительный.
* [Подсеть](../../vpc/concepts/network.md#subnet).

  {% include [GL CIDR Warning](../../_includes/managed-gitlab/cidr-note.md) %}

* Размер диска. После создания инстанса размер его диска [можно увеличить](../operations/instance/instance-update.md).
* Имя в домене `.gitlab.yandexcloud.net` — адрес вашего экземпляра {{ GL }} в интернете.
* Данные администратора:
  * Электронная почта.
  * Логин.

{% include [HTTPS info](../../_includes/managed-gitlab/note-https.md) %}


## Примеры использования {#examples}

* [{#T}](../tutorials/gitlab-lockbox-integration.md)
* [{#T}](../tutorials/ci-cd-serverless.md)
* [{#T}](../tutorials/install-gitlab-runner.md)
* [{#T}](../tutorials/gitlab-containers.md)