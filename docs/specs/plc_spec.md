# 📑 Technická špecifikácia: Projekt Studňa

## 1. Hardvér PLC (v studni): eletechsup ES32D26
- **Mikrokontrolér:** ESP32-WROOM-32U
- **Platforma:** ESP-IDF (V5.x)
- **Konfigurácia:** Framework ESP-IDF v PlatformIO alebo natívne

### 🔧 Mapovanie PINov (Kritické pre funkčnosť)

| Komponent | Funkcia | GPIO Pin | Poznámka |
| :--- | :--- | :--- | :--- |
| **Relé (74HC595)** | Data (MOSI) | **12** | |
| | Clock (SCK) | **22** | |
| | Latch (CS) | **23** | |
| | Output Enable| **13** | **MUST BE LOW** pre aktiváciu relé |
| **Vstupy (74HC165)**| Data (MISO) | **15** | |
| | Clock | **2** | |
| | Load (PL) | **0** | |
| **Analóg (AI)** | Prúd 4-20mA | **34, 39, 35, 36**| |
| | Napätie 0-10V| **14, 33, 27, 32**| |

### 🔘 Manuálny panel (6-kanálový IO port)
Tieto piny sú priamo vyvedené z ESP32 pre lokálne ovládanie:

| Periféria | Typ | GPIO Pin | Logika |
| :--- | :--- | :--- | :--- |
| **Tlačidlo REŽIM** | Vstup | **4** | Pull-up |
| **Tlačidlo REFRESH**| Vstup | **16** | Pull-up |
| **Tlačidlo FLUSH** | Vstup | **17** | Pull-up |
| **LED REŽIM** | Výstup | **18** | High = ON |
| **LED REFRESH** | Výstup | **19** | High = ON |
| **LED FLUSH** | Výstup | **21** | High = ON |

---

## 2. Hardvér Panel (v dome): Waveshare 7" Touch
- **Čip:** ESP32-S3 (8MB PSRAM)
- **Framework:** ESP-IDF
- **Grafika:** LVGL 8.x/9.x

---

## 3. Komunikačná a Logická vrstva
- **Protokol:** MQTT (Broker: `mosquitto.local`)
- **Algoritmy:** Refresh, Flush, Fail-Safe (podľa ARCHITECTURE.md)

---

## 4. Konfigurácia PlatformIO (`platformio.ini`)
```ini
[env:esp32dev]
platform = espressif32
board = esp32dev
framework = espidf
monitor_speed = 115200
# Knižnice pre ESP-IDF sa riešia cez idf_component.yml alebo submoduly
```
