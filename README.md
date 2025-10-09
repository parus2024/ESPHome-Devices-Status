# ESPHome Devices Status

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/yourusername/esphome-devices-status/blob/main/LICENSE)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-2023.10+-green.svg)](https://www.home-assistant.io/)

Это проект для **Home Assistant**, предоставляющий динамическую Lovelace-карту для мониторинга статуса устройств на базе **ESPHome**. Карта автоматически сканирует устройства ESPHome, сортирует их по онлайн/оффлайн, и позволяет отображать дополнительные метрики (uptime, WiFi-сигнал, IP-адрес) и действия (перезагрузка устройства).

## Особенности

- **Автоматическое обнаружение устройств**: Карта использует `binary_sensor` с `device_class: connectivity` для поиска устройств ESPHome.
- **Сортировка**: Возможность сортировки по `friendly_name` или `entity_id`.
- **Фильтры и переключатели**: Показывать/скрывать uptime, WiFi-сигнал, IP-адрес и кнопку перезагрузки.
- **Разделение по статусу**: Устройства разделены на "Online" и "Offline" секции.
- **Интерактивность**: Кнопки для перезагрузки устройств и переключатели для фильтров.
- **Настраиваемый дизайн**: Использует `card_mod` для кастомизации стиля (серый бордер, без тени).

## Установка

1. **Клонируйте репозиторий** или скачайте файлы:
   ```bash
   git clone https://github.com/yourusername/esphome-devices-status.git
   ```

2. **Добавьте в Home Assistant**:
   - Убедитесь, что у вас установлены интеграции ESPHome и необходимые кастомные компоненты (см. Зависимости).
   - Скопируйте содержимое файла `esphome_devices_status.yaml` (или аналогичного) в ваш `ui-lovelace.yaml` или добавьте как новую карту в интерфейсе Lovelace.
   - Если используется `auto-entities`, убедитесь, что оно установлено.

3. **Настройте устройства ESPHome**:
   - Ваши устройства должны иметь `binary_sensor` с `device_class: connectivity` (например, `esphome_device_status`).
   - Дополнительные сенсоры: `sensor.esphome_device_uptime`, `sensor.esphome_device_wifi_signal`, `sensor.esphome_device_esp_ip_address`.
   - Кнопка: `button.esphome_device_esp_reboot`.

## Использование

- **Добавьте карту в дашборд**: В Lovelace UI выберите "Manual card" и вставьте YAML-конфигурацию.
- **Переключатели**:
  - `Uptime`: Показывает время работы устройства.
  - `WiFi`: Уровень сигнала WiFi.
  - `IP`: IP-адрес устройства.
  - `Reboot`: Кнопка для перезагрузки (требует `button` entity).
- **Сортировка**: Используйте `input_select.esphome_sort_by` для выбора способа сортировки (по имени или ID).
- **Статус**: Карта обновляется автоматически при изменении статуса устройств.

## Конфигурация

Карта использует следующие сущности (убедитесь, что они существуют в вашем Home Assistant):

- `input_select.esphome_sort_by` (опции: `friendly_name`, `entity_id`).
- `input_boolean.show_uptime`, `input_boolean.show_wifi`, `input_boolean.show_ip`, `input_boolean.show_reboot` — переключатели фильтров.
- Сенсоры устройств: `binary_sensor.*_status`, `sensor.*_uptime`, `sensor.*_wifi_signal`, `sensor.*_esp_ip_address`.
- Кнопки: `button.*_esp_reboot`.

## Зависимости

- **Home Assistant** версии 2023.10+.
- **HACS** (Home Assistant Community Store) для установки кастомных компонентов:
  - [card-mod](https://github.com/thomasloven/lovelace-card-mod) — для стилизации.
  - [auto-entities](https://github.com/thomasloven/lovelace-auto-entities) — для динамического списка.
  - [multiple-entity-row](https://github.com/benct/lovelace-multiple-entity-row) — для группировки сущностей.
- **ESPHome** интеграция в Home Assistant.
- Ваши устройства ESPHome должны быть настроены с соответствующими сенсорами (см. [документацию ESPHome](https://esphome.io/)).

## Скриншоты

(Добавьте скриншоты вашего дашборда здесь, например, через GitHub Issues или wiki. Пример: изображение карты с онлайн/оффлайн устройствами и фильтрами.)

## Вклад в проект

Вклад приветствуется! Если вы хотите улучшить проект:
1. Fork репозиторий.
2. Создайте ветку для ваших изменений.
3. Отправьте Pull Request с описанием.

Для багов или идей откройте Issue на GitHub.

## Лицензия

Этот проект распространяется под лицензией MIT. Подробности в файле [LICENSE](LICENSE).

## Контакты

- Telegram: [https://telegram.org/](https://t.me/parus_smart)
