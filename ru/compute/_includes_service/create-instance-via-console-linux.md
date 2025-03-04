Чтобы создать виртуальную машину:
1. В [консоли управления]({{ link-console-main }}) выберите каталог, в котором будет создана виртуальная машина.
1. В списке сервисов выберите **{{ compute-name }}**.
1. Нажмите кнопку **Создать ВМ**.
1. В блоке **Базовые параметры**:
    - Введите имя и описание ВМ. Требования к имени:

        {% include [name-format](../../_includes/name-format.md) %}

        {% include [name-fqdn](../../_includes/compute/name-fqdn.md) %}

    - Выберите [зону доступности](../../overview/concepts/geo-scope.md), в которой будет находиться виртуальная машина.
1. В блоке **Образы из {{ marketplace-name }}** выберите один из [образов](../operations/images-with-pre-installed-software/get-list.md) и версию операционной системы на базе Linux.
1. (опционально) В блоке **Диски** настройте загрузочный диск:
      - Укажите нужный размер диска.
      - Выберите [тип диска](../concepts/disk.md#disks_types).

   Если вы хотите создать виртуальную машину из существующего диска, в блоке **Диски** [добавьте диск](../operations/vm-create/create-from-disks.md).
1. В блоке **Вычислительные ресурсы**:
    - Выберите [платформу](../concepts/vm-platforms.md).
    - Укажите [гарантированную долю](../../compute/concepts/performance-levels.md) и необходимое количество vCPU, а также объем RAM.
    - При необходимости сделайте виртуальную машину [прерываемой](../concepts/preemptible-vm.md).
    - (опционально) Включите [программно-ускоренную сеть](../concepts/software-accelerated-network.md).
1. В блоке **Сетевые настройки**:
    - Укажите идентификатор подсети или выберите [облачную сеть](../../vpc/concepts/network.md#network) из списка. Если сети нет, нажмите кнопку **Создать новую сеть** и создайте ее:
        - В открывшемся окне укажите имя новой сети и выберите, к какой подсети необходимо подключить виртуальную машину. У каждой сети должна быть как минимум одна [подсеть](../../vpc/concepts/network.md#subnet) (если подсети нет, создайте ее). Затем нажмите кнопку **Создать**.
    - В поле **Публичный адрес** выберите способ назначения адреса:
        - **Автоматически** — чтобы назначить случайный IP-адрес из пула адресов {{ yandex-cloud }}.
        - **Список** — чтобы выбрать публичный IP-адрес из списка зарезервированных заранее статических адресов. Подробнее читайте в разделе [{#T}](../../vpc/operations/set-static-ip.md).
        - **Без адреса** — чтобы не назначать публичный IP-адрес.
    - (опционально) Создайте запись для ВМ в [зоне DNS](../../dns/concepts/dns-zone.md). Разверните блок **Настройки DNS для внутренних адресов** и укажите зону, FQDN и время жизни записи. Подробнее см. [Интеграция Cloud DNS с Compute Cloud](../../dns/concepts/compute-integration.md). 
    - (опционально) Выберите опцию [защиты от DDoS-атак](../../vpc/ddos-protection/).
1. В блоке **Доступ** укажите данные для доступа на виртуальную машину:
   
    - (опционально) Выберите или создайте [сервисный аккаунт](../../iam/concepts/users/service-accounts.md). Использование сервисного аккаунта позволяет гибко настраивать права доступа к ресурсам.
     
    - В поле **Логин** введите имя пользователя.

      {% note alert %}

      Не используйте логин `root` или другие имена, зарезервированные операционной системой. Для выполнения операций, требующих прав суперпользователя, используйте команду `sudo`.

      {% endnote %}

    - В поле **SSH-ключ** вставьте содержимое файла [открытого ключа](../operations/vm-connect/ssh#creating-ssh-keys).
   
1. Нажмите кнопку **Создать ВМ**. 

Виртуальная машина появится в списке. При создании виртуальной машине назначаются [IP-адрес](../../vpc/concepts/address) и [имя хоста](../../vpc/concepts/address#fqdn) (FQDN).