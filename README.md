# 🖱️ ESP32 Air Mouse & Presentation Remote

Bezprzewodowy kontroler przestrzenny (mysz żyroskopowa) do komputera PC, inspirowany rozwiązaniem LG Magic Remote. Projekt realizowany w ramach laboratorium projektowego.

## 📌 Główne funkcjonalności
- **Sterowanie kursorem w powietrzu:** Mapowanie wskazań żyroskopu (MPU-6050) na ruch w osiach X i Y.
- **Filtracja drżenia (Deadzone):** Eliminacja mimowolnego mikrodrżenia dłoni.
- **Dynamiczna akceleracja:** Precyzyjne ruchy przy małych prędkościach, szybkie przeskoki ekranu przy gwałtownych gestach.
- **Przycisk funkcyjny (Clutch / Scroll):** Zamrażanie ruchu kursora oraz tryb przewijania stron ruchem dłoni.
- **Komunikacja Plug & Play:** Urządzenie emuluje standardową mysz BLE HID (działa na Windows/Linux/macOS bez dodatkowych sterowników).

## 🛠️ Wykorzystany sprzęt
- **Mikrokontroler:** ESP32 NodeMCU (BLE 4.2)
- **Czujnik IMU:** 6-osiowy MPU-6050 (akcelerometr + żyroskop)
- **Przyciski:** 3x tact-switch (LPM, PPM, Przycisk funkcyjny)
- **Zasilanie:** Akumulator Li-Po + moduł ładowania TP4056

## 🔌 Schemat połączeń (Pinout)
- `MPU-6050 SDA` -> `ESP32 GPIO 21`
- `MPU-6050 SCL` -> `ESP32 GPIO 22`
- `LPM (Lewy Przycisk)` -> `ESP32 GPIO 18` (do GND)
- `PPM (Prawy Przycisk)` -> `ESP32 GPIO 19` (do GND)
- `Przycisk Funkcyjny` -> `ESP32 GPIO 23` (do GND)

## 📅 Harmonogram i Kamienie Milowe
- [x] Dobór komponentów i analiza założeń (SMART)
- [ ] Uruchomienie odczytu z MPU-6050 i bazowa emulacja BLE HID (Faza 1)
- [ ] Implementacja deadzone, akceleracji i trybu scroll (Faza 2)
- [ ] Projekt i wydruk obudowy 3D oraz montaż zasilania Li-Po (Faza 3)
- [ ] Testy użytkowe i dokumentacja końcowa (Faza 4)
