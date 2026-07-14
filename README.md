# Romo Download Manager (Android)

Production-oriented Android download manager built with Kotlin, Jetpack Compose (Material 3), MVVM, and Clean Architecture.

## Tech Stack
- Kotlin
- Jetpack Compose + Material 3
- MVVM + Clean Architecture
- Min SDK 29 / Target SDK 35
- Foreground Service for background downloads
- MediaStore Storage APIs
- OkHttp for networking

## Project Structure
```
app/src/main/java/com/romo/downloadmanager
├── data
│   ├── download
│   │   ├── DownloadEngine.kt
│   │   └── FileStorageManager.kt
│   ├── repository
│   │   └── DownloadRepositoryImpl.kt
│   └── service
│       └── DownloadForegroundService.kt
├── di
│   └── AppContainer.kt
├── domain
│   ├── model
│   │   ├── DownloadItem.kt
│   │   └── DownloadStatus.kt
│   ├── repository
│   │   └── DownloadRepository.kt
│   └── usecase
│       └── DownloadUseCases.kt
├── presentation
│   ├── screen
│   │   └── DownloadScreen.kt
│   ├── theme
│   │   ├── Color.kt
│   │   ├── Theme.kt
│   │   └── Type.kt
│   └── viewmodel
│       └── DownloadViewModel.kt
├── util
│   └── Formatters.kt
├── DownloadManagerApplication.kt
└── MainActivity.kt
```

## Feature Coverage
- Add direct URL manually
- Multiple concurrent downloads
- Live progress percentage
- Download speed (bytes/sec)
- Downloaded/total size view
- Pause / Resume / Cancel / Retry
- Background downloading via Foreground Service
- Ongoing progress notification
- Save files to Downloads via MediaStore
- MIME/file type detection
- Open downloaded files via Android intents
- Dark mode support

## Architecture Explanation
- **Domain layer** defines business models, repository contract, and use-cases.
- **Data layer** implements download orchestration (`DownloadEngine`), storage (`FileStorageManager`), and app-facing repository implementation.
- **Presentation layer** manages state in `DownloadViewModel` and renders Compose UI in `DownloadScreen`.
- **Service layer** (`DownloadForegroundService`) keeps downloads running in the background with notifications.
- **DI container** (`AppContainer`) wires dependencies without framework lock-in.

## Permissions
Declared in `AndroidManifest.xml`:
- `INTERNET`
- `FOREGROUND_SERVICE`
- `FOREGROUND_SERVICE_DATA_SYNC`
- `POST_NOTIFICATIONS`

## Build
This repository includes Gradle Kotlin DSL configuration for Android app setup.
