<div align="center">
  <h1>SoOoMa IPTV for tvOS</h1>
  <p>
    <strong>A high-performance, fully native tvOS client for IPTV services, built entirely in Swift 6.</strong>
  </p>
  <p>
    <a href="#features">Features</a> •
    <a href="#architecture">Architecture</a> •
    <a href="#installation">Installation</a> •
    <a href="#license">License</a>
  </p>
</div>

---

SoOoMa is a modern, blazing fast IPTV client designed specifically for Apple TV (tvOS). Built natively using **SwiftUI**, **SwiftData**, and **Swift 6 Strict Concurrency**, it delivers a buttery smooth experience for Live TV, Movies (VOD), and Series. 

Under the hood, it leverages a highly optimized **libmpv** rendering stack and supports multi-device synchronization via **CloudKit**.

## 🌟 Features

- **Multi-Protocol Support**: Seamlessly stream from **Xtream Codes** (JSON API), **Stalker Portals** (MAC-based auth), and **M3U Playlists**.
- **High-Performance Playback**: Powered by `libmpv` and `AVSampleBufferDisplayLayer` for robust, format-agnostic video decoding.
- **iCloud Sync**: Automatically syncs your configured accounts across all your Apple devices using a secure, private CloudKit database.
- **Remote Web Server**: Built-in HTTP web server allowing you to manage your accounts and settings remotely from any web browser on your network.
- **Advanced Caching & Persistence**: Employs a dual-store SwiftData architecture to separate heavy, high-churn content (EPG/VODs) from lightweight, syncable data (Accounts), preventing CloudKit quota exhaustion.
- **Robust Media Handling**: Custom SSL-bypassing image pipelines to handle self-signed certificates commonly found on IPTV providers, backed by memory and disk caching via Kingfisher.

## 🎫 Support Tickets

If you encounter any bugs, need help, or have feature requests, please submit a support ticket via our Issue Tracker:

👉 **[Submit a Support Ticket](https://github.com/SeMoOo/SoOoMa-TV-Support/issues/new/choose)**

## 📸 Screenshots

| Startup & Login | Home Dashboard | Category Selection | Video Player & EPG |
|:---:|:---:|:---:|:---:|
| <img src="screenshot_login.png" width="200" /> | <img src="screenshot_dashboard.png" width="200" /> | <img src="screenshot_category.png" width="200" /> | <img src="screenshot_player.png" width="200" /> |

## 🛠 Tech Stack

- **Framework**: SwiftUI (tvOS 26.0+)
- **Language**: Swift 6 (Strict Concurrency enabled)
- **Database**: SwiftData (CloudKit + Local Stores)
- **Video Player**: `libmpv` / `MPVKit`
- **Dependency Manager**: CocoaPods & Swift Package Manager (SPM)

## 🚀 Installation & Build Instructions

### Prerequisites
- macOS with Xcode 17+
- CocoaPods installed (`sudo gem install cocoapods`)
- tvOS 26.0 SDK

### Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/IPTV.git
   cd IPTV
   ```

2. **Install dependencies**:
   Because the project utilizes `swift-mdk`, dependencies must be resolved via CocoaPods.
   ```bash
   pod install
   ```
   *(Note: MPVKit and Kingfisher are resolved through SPM automatically by Xcode).*

3. **Open the Workspace**:
   Open `IPTV.xcworkspace` in Xcode.

4. **Build & Run**:
   Select the **IPTV** scheme and choose an Apple TV Simulator (or physical device), then press `Cmd + R`.

## 🏗 Architecture Overview

SoOoMa employs several advanced architectural patterns tailored for the demands of IPTV streaming:

- **Dual SwiftData Stores**: A single `ModelContainer` encapsulates two configurations:
  - `Cloud`: Syncs `XCAccount` securely via CloudKit.
  - `Local`: Stores all heavy metadata (`LiveChannel`, `Movie`, `Series`, `Category`) strictly on-device to maximize performance and avoid iCloud rate limits.
- **Unified Sync Protocol**: The `SyncProtocol` abstracts Xtream, Stalker, and M3U synchronization behind a single interface, managed by a `@MainActor` `SyncEngine`.
- **MainActor Isolation**: Ensures strict UI thread safety, with all data parsing and rendering operations safely hopping boundaries without blocking the interface.

## 📄 License

**© 2026 Bassam Zaidan. All Rights Reserved.**

This is a proprietary, closed-source commercial application. 
You may not copy, modify, distribute, sell, or lease any part of this software without explicit written permission.

See the [LICENSE.md](LICENSE.md) file for full details.
