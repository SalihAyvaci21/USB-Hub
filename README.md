# USB Hub + PD Controller Projesi

Bu proje, USB-C PD (Power Delivery) desteği ile çalışan, 5V-24V arası giriş voltajını kabul eden ve gücü dört farklı çıkışa dağıtan bir **USB Hub** tasarımıdır. Güç ve sinyal yönetimi için çeşitli koruma ve anahtarlama IC’leri entegre edilmiştir.

## 📦 Özellikler

- **Giriş Voltajı (USB-C):** 5V - 24V (PD destekli)
- **Çıkışlar:**
  - 1x **USB-A 3.0**
  - 1x **USB-C 3.0**
  - 1x **FTDI (UART-USB dönüştürücü)**
  - 1x **ST-Link (Programlayıcı / Debugger)**
- **PD Controller:** CH224K (Switch ile kontrol)
- **USB Hub IC:** TUSB8044ARGCR
- **Sinyal Yönlendirme:**
  - 2x HD3SS3202IRSVR (SS MUX, C-to-A ve A-to-C için)
- **Koruma Devreleri:**
  - TPD6S300A (ESD ve güç koruması)
- **Güç Regülasyonu:**
  - 1.1V: TLV71211 (SOT23-5)
  - 3.3V: NCP1117-3.3 (SOT-223)
  - 5V: KA78M05 (TO-252)
- **Programlayıcılar:**
  - ST-Link için STM32F103CBTx
  - FTDI için FT232RL-REEL

## 🛠 Bileşenler

| Bileşen                  | Açıklama                        |
|-------------------------|------------------------------------|
| **CH224K**              | USB-C PD Controller              |
| **TUSB8044ARGCR**       | USB 3.0 Hub Controller            |
| **HD3SS3202IRSVR**      | USB SS MUX (C/A anahtarlama)      |
| **TPD6S300A**           | USB-C koruma (ESD, VBUS)          |
| **TLV71211**            | 1.1V LDO Regülatör                |
| **NCP1117-3.3**         | 3.3V LDO Regülatör                |
| **KA78M05**             | 5V Regülatör                      |
| **STM32F103CBTx**       | ST-Link Programlayıcı MCU         |
| **FT232RL-REEL**        | FTDI USB-UART dönüştürücü         |

## 📐 Tasarım Özellikleri

- **PD Desteği:** 5V ila 24V arası giriş voltajını otomatik algılar entegre doğru çıkışı verir.
- **Güç Dağıtımı:** TUSB8044ARGCR ile USB 3.0 sinyalleri dört porta bölünür.
- **Sinyal Yönlendirme:** HD3SS3202 ile USB-C ve USB-A arasında yüksek hızlı sinyal yönlendirme.
- **Güvenlik:** TPD6S300A ile USB-C girişinde aşırı gerilim ve ESD koruması.
- **Programlama ve Debug:** Dahili ST-Link (STM32F103CBTx) ve FTDI (FT232RL) arayüzleri.

## 🔌 Kullanım

1. **Giriş Bağlantısı:**
   - USB-C PD girişine adaptör bağlayın (5V-24V arası desteklenir).
2. **Çıkışlar:**
   - USB-A 3.0 portuna cihaz bağlanabilir.
   - USB-C 3.0 portu yüksek hızlı veri aktarımı için kullanılabilir.
   - FTDI portu UART bağlantısı için kullanılabilir.
   - ST-Link portu STM32 debug/programlama için hazırdır.

## ⚡ Koruma ve Güvenlik

- **ESD Koruma:** TPD6S300A
- **Aşırı Gerilim:** PD kontrolcü ile voltaj sınırlaması
- **Sinyal Integrity:** SS MUX ile minimum sinyal kaybı

## 📁 Dosyalar

- `Usb 3. v11.kicad_pro` – KiCAD proje dosyası
- `Usb 3. v11.kicad_sch` – Devre şeması
- `gerber` – Üretim için Gerber dosyaları 
- `BomList.xlsx` – Parça listesi

## ⚠️ Dikkat

> Bu tasarım yüksek hızlı USB sinyalleri ve PD voltajları içerir. Geliştirme ve test sırasında uygun yalıtım ve ESD önlemleri alınmalıdır.

## 📜 Lisans

Bu proje açık kaynaklıdır ve kişisel/akademik kullanım için serbesttir.

---

# USB Hub + PD Controller Project

This project is a **USB Hub** design that operates with USB-C PD (Power Delivery) support, accepting an input voltage range of 5V-24V and distributing power across four different outputs. Various protection and switching ICs are integrated for power and signal management.

## 📦 Features

- **Input Voltage (USB-C):** 5V - 24V (PD supported)
- **Outputs:**
  - 1x **USB-A 3.0**
  - 1x **USB-C 3.0**
  - 1x **FTDI (UART-USB converter)**
  - 1x **ST-Link (Programmer / Debugger)**
- **PD Controller:** CH224K (controlled via switch)
- **USB Hub IC:** TUSB8044ARGCR
- **Signal Routing:**
  - 2x HD3SS3202IRSVR (SS MUX for C-to-A and A-to-C)
- **Protection Circuits:**
  - TPD6S300A (ESD and power protection)
- **Power Regulation:**
  - 1.1V: TLV71211 (SOT23-5)
  - 3.3V: NCP1117-3.3 (SOT-223)
  - 5V: KA78M05 (TO-252)
- **Programmers:**
  - STM32F103CBTx for ST-Link
  - FT232RL-REEL for FTDI

## 🛠 Components

| Component              | Description                         |
|------------------------|-------------------------------------|
| **CH224K**             | USB-C PD Controller                 |
| **TUSB8044ARGCR**      | USB 3.0 Hub Controller              |
| **HD3SS3202IRSVR**     | USB SS MUX (C/A switching)          |
| **TPD6S300A**          | USB-C protection (ESD, VBUS)        |
| **TLV71211**           | 1.1V LDO Regulator                  |
| **NCP1117-3.3**        | 3.3V LDO Regulator                  |
| **KA78M05**            | 5V Regulator                        |
| **STM32F103CBTx**      | ST-Link Programmer MCU              |
| **FT232RL-REEL**       | FTDI USB-UART Converter             |

## 📐 Design Features

- **PD Support:** Automatically detects input voltage between 5V and 24V and provides appropriate regulated output.
- **Power Distribution:** USB 3.0 signals are distributed to four ports using TUSB8044ARGCR.
- **Signal Routing:** High-speed signal switching between USB-C and USB-A via HD3SS3202.
- **Protection:** Overvoltage and ESD protection on USB-C input using TPD6S300A.
- **Programming and Debugging:** Integrated ST-Link (STM32F103CBTx) and FTDI (FT232RL) interfaces.

## 🔌 Usage

1. **Input Connection:**
   - Connect an adapter to the USB-C PD input (supports 5V-24V).
2. **Outputs:**
   - USB-A 3.0 port can connect to devices.
   - USB-C 3.0 port supports high-speed data transfer.
   - FTDI port can be used for UART connections.
   - ST-Link port is ready for STM32 debugging/programming.

## ⚡ Protection and Safety

- **ESD Protection:** TPD6S300A
- **Overvoltage:** Voltage limitation via PD controller
- **Signal Integrity:** Minimal signal loss using SS MUX

## 📁 Files

- `Usb 3. v11.kicad_pro` – KiCAD project file
- `Usb 3. v11.kicad_sch` – Schematic file
- `gerber` – Gerber files for production
- `BomList.xlsx` – Bill of Materials

## ⚠️ Warning

> This design involves high-speed USB signals and PD voltages. Proper insulation and ESD precautions must be taken during development and testing.

## 📜 License

This project is open-source and free for personal and academic use.

