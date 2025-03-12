# BlueControl - Bluetooth Control App

BlueControl is a modern Android application built with Kotlin and Jetpack Compose that enables seamless connectivity and control of Bluetooth Low Energy (BLE) devices. It provides an intuitive and interactive interface for scanning, connecting, and exchanging data using a JSON-based communication protocol.

---

## 🚀 Features

- **🔍 Real-time Device Scanning** – Discover nearby BLE devices with an intuitive UI.
- **🔗 Secure Connection Management** – Automatically reconnect to BLE devices upon disconnection.
- **🛠 Interactive Control Panel** – Send and receive multiple parameters seamlessly.
- **📊 Live Data Monitoring** – View real-time device updates.
- **🎨 Modern UI with Material 3** – Smooth animations and intuitive controls.
- **📡 Parameter Monitoring** – Track current, voltage, frequency, left/right frequency, and volume.

---

## 📸 Screenshots


### 📱 Home Screen  
![Home Screen](Home.jpeg)

### 🔍 Device Scanning  
![Device Scanning](Usage_New_UI.jpeg)

### 📊 Live Data Monitoring  
![Live Data](Usage_New_UI_II.jpeg)


---

## 🏗 Technical Overview

### ⚙️ Architecture

BlueControl follows a clean architecture pattern:
- **`BluetoothViewModel`** – Manages Bluetooth connectivity and data processing.
- **`TestBluetoothScreen`** – Jetpack Compose UI layer for user interaction.
- **Data Layer** – Handles user preferences and device storage.

### 🔵 BLE Communication

The app exchanges JSON-formatted messages for consistent data communication:

```json
{
  "C": "current_value",
  "V": "voltage_value",
  "F": "frequency_value",
  "L": "left_frequency_value",
  "R": "right_frequency_value",
  "VOL": "volume_value"
}
```

### 🎨 UI Components

- **Material 3** with a custom color scheme.
- **Adaptive cards** for device scanning and control.
- **Real-time status indicators** for device connectivity.
- **Smooth animations** for an enhanced user experience.

---

## 🏁 Getting Started

### 📋 Prerequisites

- Android Studio Arctic Fox (2021.3.1) or newer.
- Android SDK 21+.
- Kotlin 1.5.0+.

### 🔑 Required Permissions

Ensure the following permissions are included in your `AndroidManifest.xml`:

```xml
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.BLUETOOTH_CONNECT" />
<uses-permission android:name="android.permission.BLUETOOTH_SCAN" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
```

### 📥 Installation

1. Clone this repository:
   ```sh
   git clone https://github.com/your-repo/BlueControl.git
   ```
2. Open the project in Android Studio.
3. Build and run the application on a physical Android device (BLE is not fully supported on emulators).

---

## 📖 Usage

1. **Launch the app** and grant the necessary permissions.
2. **Start scanning** to discover nearby BLE devices.
3. **Select a device** from the list to establish a connection.
4. **Use the control panel** to:
   - Monitor real-time device parameters.
   - Adjust values and send updates.
   - Request the latest device readings.

---

## ⚙️ Customization

### 🔧 BLE UUIDs
Modify UUIDs in `BluetoothViewModel.kt` to match your BLE device:

```kotlin
// Service UUID
private val SERVICE_UUID = UUID.fromString("0000FFF0-0000-1000-8000-00805F9B34FB")

// Characteristic UUIDs for reading data
private val CHARACTERISTIC_READ_CURRENT_UUID = UUID.fromString("0000FFA2-0000-1000-8000-00805F9B34FB")
private val CHARACTERISTIC_READ_VOLTAGE_UUID = UUID.fromString("0000FFB2-0000-1000-8000-00805F9B34FB")
private val CHARACTERISTIC_READ_FREQUENCY_UUID = UUID.fromString("0000FFC2-0000-1000-8000-00805F9B34FB")
private val CHARACTERISTIC_READ_LEFT_FREQ_UUID = UUID.fromString("0000FFD2-0000-1000-8000-00805F9B34FB")
private val CHARACTERISTIC_READ_RIGHT_FREQ_UUID = UUID.fromString("0000FFE2-0000-1000-8000-00805F9B34FB")
private val CHARACTERISTIC_READ_VOLUME_UUID = UUID.fromString("0000FFF2-0000-1000-8000-00805F9B34FB")

// Characteristic UUIDs for writing data
private val CHARACTERISTIC_WRITE_UUID = UUID.fromString("0000FF01-0000-1000-8000-00805F9B34FB")

// Descriptor UUID
private val CLIENT_CHARACTERISTIC_CONFIG_UUID = UUID.fromString("00002902-0000-1000-8000-00805F9B34FB")

```

### 🎨 UI Theme
Customize colors in `TestBluetoothScreen.kt`:

```kotlin
// Primary Theme Colors
private val BluetoothPrimary = Color(0xFF3F51B5) // Indigo
private val BluetoothPrimaryVariant = Color(0xFF303F9F) // Darker Indigo
private val BluetoothSecondary = Color(0xFF03A9F4) // Light Blue
private val BluetoothSecondaryVariant = Color(0xFF0288D1) // Darker Blue

// Background & Surface Colors
private val BackgroundColor = Color(0xFFF5F5F5) // Light Gray
private val SurfaceColor = Color(0xFFFFFFFF) // White

// Text Colors
private val TextPrimary = Color(0xFF212121) // Dark Gray
private val TextSecondary = Color(0xFF757575) // Medium Gray

// Status Indicator Colors
private val SuccessColor = Color(0xFF4CAF50) // Green
private val WarningColor = Color(0xFFFFC107) // Amber
private val ErrorColor = Color(0xFFF44336) // Red

```

---

## 🏗 How It Works

1. **Device Discovery** – The app scans for nearby BLE devices.
2. **Connection Establishment** – It connects via Bluetooth GATT.
3. **Service & Characteristic Discovery** – Reads available services.
4. **Data Exchange** – JSON-formatted messages update in real-time.

---

