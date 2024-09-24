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
![Screenshot from 2024-09-24 19-03-23](https://github.com/user-attachments/assets/d4aaad90-cea1-4c38-8233-562a01cf5a7f)

- `make -j6 modules`
![Screenshot from 2024-09-24 19-05-27](https://github.com/user-attachments/assets/0d1e7669-b786-4dd9-b51e-4ebeb7a36dcb)

- `make modules_install`
![Screenshot from 2024-09-24 19-06-27](https://github.com/user-attachments/assets/4741fb3c-2ac4-40cd-bd85-9910b58b2835)

- `make install`
![Screenshot from 2024-09-24 19-07-20](https://github.com/user-attachments/assets/0d5da1eb-12c9-4039-bd18-a600950a26e3)

## Содержимое папки /boot
![Screenshot from 2024-09-24 19-08-15](https://github.com/user-attachments/assets/19245876-7662-4124-bcdf-d22da5d5066f)

## Запуск ОС
![task](https://github.com/user-attachments/assets/38b12149-2cbe-4b95-8c35-264294b1a384)

![Screenshot from 2024-09-24 19-19-15](https://github.com/user-attachments/assets/765b6f51-65bf-4878-8e4b-bf05979824ab)

## Результаты тестирования
После запуска нового ядра были протестированны:
- Видео драйвер (GUI)
- Аудио драйвер (видео в браузере)
- Драйвер сетевой карты (утилита `ping`, браузер)
- Bluetooth (подключение Bluetooth устройства)

