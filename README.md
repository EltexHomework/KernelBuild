# Задание 17 - Сборка ядра Linux
## Задания
Собрать vanilla версию ОС Linux. Конфигурацию проводить с defconfig (стандартная конфигурация).

## Конфигурация 
Для создания конфигурационного файла были использованы утилиты:
- `make defconfig` - создание стандартной конфигурации
- `make menuconfig` - открытие контекстного меню на ncurses для удобной настройки конфигурации
### Внесенные изменения в конфигурацию
В стандартную конфигурацию ядра Linux были внесены следующие изменения:
- Добавление префикса локальной версии EndVersion
- Включен флаг General Notification Queue
- Core Scheduling for SMT
- Multi-core scheduler support
- Power Management Debug Support (При запуске нового ядра появляется ошибка о запуске power manager daemon, были попытки её исправить)
- Kernel support for ELF binaries
- Page allocater randomization
- Bluetooth Support
- NVME Support (Для работы с SSD типа NVME).
- PCI Sound devices: Intel/SiS/nVidia/AMD/ALi AC97 Controller
- Generic sound devices: PC-Speaker support
### Сборка ядра
Сборка ядра осуществлялась при помощи следующих утилит:
- `make -j6 bzImage` - сборка большого образа на 6-ти ядрах
- `make -j6 modules` - сборка модулей на 6-ти ядрах
- `make modules_install` - установка модулей
- `make install` - установка ядра

## Результаты выода при последней сборке
- `make -j6 bzImage`

- `make -j6 modules`

- `make modules_install`

- `make install`

## Содержимое папки /boot

## Запуск ОС

## Результаты тестирования
После запуска нового ядра были протестированны:
- Видео драйвер (GUI)
- Аудио драйвер (видео в браузере)
- Драйвер сетевой карты (утилита `ping`, браузер)
- Bluetooth (подключение Bluetooth устройства)

