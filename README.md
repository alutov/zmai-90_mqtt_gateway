# Альтернативная прошивка ZMAi-90 с поддержкой Mqtt.
### ENG<br>
[Use Google to translate into English.](https://translate.google.com/translate?hl=ru&sl=ru&tl=en&u=https%3A%2F%2Fgithub.com%2Falutov%2Fzmai-90_mqtt_gateway%2Fblob%2Fmaster%2FREADME.md)<br>
### RUS<br>
&emsp; В Mqtt выводится 4 основных параметра: напряжение, ток, мощность и потребленная энергия. Для синхронизации показаний энергии со счетчиком коммерческого учета предусмотрена опция Еnergy offset. Значение из этого поля добавляется(или вычитается) к текущим показаниям при выводе в Mqtt. Доступно управление реле как кнопкой, так и по Mqtt. Поддерживается Home Assistant Mqtt Discovery. Прошивка рассчитана на работу с новой ревизией ZMAi-90, в которой TYWE3S использует для управления устройством только последовательный порт. Файл fzmai.bin в папке build это уже собранный бинарник для TYWE3S (esp8266) с памятью 1 Мбайт и прошивается одним файлом с адреса 0x0000 на чистую TYWE3S. Вместо него также можно использовать три стандартных файла для перепрошивки: bootloader.bin (адрес 0x1000),  partitions.bin (адрес 0x8000) и zmai.bin (адрес 0x10000). Файл zmai.bin можно также использовать для обновления прошивки через web интерфейс. Затем нужно создать гостевую сеть Wi-Fi в роутере с ssid "zmai" и паролем "12345678", подождать, пока TYWE3S не подключится к нему, ввести TYWE3S IP-адрес в веб-браузере и во вкладке Setting установить остальные параметры. После чего гостевая сеть больше не нужна. TYWE3S будет пытаться подключиться к сети "zmai" только при недоступности основной сети, например, при неправильном пароле. Если не удается подключиться и к гостевой сети, TYWE3S перезагружается. Предусмотрена возможность подключения к одному MQTT серверу нескольких ZMAi-90. Для этого нужно в каждом устройстве установить свой ZMAi-90 Number. Устройство с номером 0 будет писать в топик zmai/..., с номером 1 - zmai1/... и т.д. 
