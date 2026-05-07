# SampleApp

A modern Android application with Firebase integration and CI/CD pipeline support.

## Project Overview

**SampleApp** is an Android application built with:
- **Target API Level**: 34 (Android 14)
- **Minimum API Level**: 23 (Android 6.0)
- **Build System**: Gradle with Android Gradle Plugin 8.2.0
- **Backend Services**: Firebase Analytics

## Prerequisites

Before you begin, ensure you have the following installed:

- **Java Development Kit (JDK)**: Version 11 or higher
- **Android SDK**: Installed via Android Studio or command-line tools
- **Gradle**: Included via Gradle Wrapper (gradlew)
- **Android Studio**: Recommended for development (version 2024.1 or later)

## Project Structure

```
test-android-cicd/
├── app/
│   ├── src/
│   │   └── main/
│   │       ├── java/com/example/app/
│   │       │   └── MainActivity.java
│   │       ├── res/
│   │       │   └── layout/
│   │       │       └── activity_main.xml
│   │       └── AndroidManifest.xml
│   ├── build.gradle
│   └── google-services.json
├── gradle/
│   └── wrapper/
├── build.gradle
├── gradle.properties
├── gradlew
└── settings.gradle
```

## Getting Started

### 1. Clone the Repository

```bash
git clone <repository-url>
cd test-android-cicd
```

### 2. Configure Firebase

Ensure the `google-services.json` file is present in the `app/` directory. This file is required for Firebase integration.

If you need to set up Firebase:
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new project or use an existing one
3. Add an Android app to your Firebase project
4. Download the `google-services.json` file
5. Place it in the `app/` directory

### 3. Build the Project

```bash
# Using Gradle Wrapper (recommended)
./gradlew build

# Or using Android Studio
# File → Sync Now
```

### 4. Run the Application

#### Using Android Studio
1. Open the project in Android Studio
2. Select an emulator or connect a physical device
3. Click **Run** (Shift + F10) or select **Run → Run 'app'**

#### Using Command Line
```bash
# Build and run on connected device/emulator
./gradlew installDebug
./gradlew connectedAndroidTest
```

## Dependencies

### Core Android Dependencies
- `androidx.appcompat:appcompat:1.6.1` - AppCompat support library for Material Design and backward compatibility

### Firebase
- Firebase BOM (Bill of Materials) `34.12.0`
- Firebase Analytics - For tracking user events and app performance

## Build Configuration

### Debug Build
- Default build type
- Suitable for development and testing
- Debuggable with verbose logging

### Release Build
- Signed with a keystore for distribution
- Requires environment variables:
  - `KEYSTORE_PASSWORD` - Password for the keystore
  - `KEY_ALIAS` - Alias of the signing key
  - `KEY_PASSWORD` - Password for the signing key

Example for signed release build:
```bash
export KEYSTORE_PASSWORD=your_password
export KEY_ALIAS=your_alias
export KEY_PASSWORD=your_key_password

./gradlew assembleRelease
```

## Development

### Key Files to Modify

- **MainActivity.java** - Main entry point of the application
- **activity_main.xml** - Layout file for the main activity
- **AndroidManifest.xml** - App configuration and permissions
- **build.gradle** - App-level dependencies and build configuration

### Adding Permissions

Edit `AndroidManifest.xml` to add required permissions:

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## Testing

```bash
# Run unit tests
./gradlew test

# Run instrumented tests on a device/emulator
./gradlew connectedAndroidTest
```

## CI/CD Pipeline

This project includes CI/CD support. The repository structure suggests integration with mobile CI/CD systems. Ensure environment variables are properly configured for automated builds and deployments.

### Required Environment Variables for CI/CD
- `KEYSTORE_PASSWORD` - Keystore password for signing
- `KEY_ALIAS` - Key alias for signing
- `KEY_PASSWORD` - Key password for signing

## Troubleshooting

### Gradle Sync Issues
```bash
./gradlew clean
./gradlew sync
```

### Build Failures
1. Clear build cache:
   ```bash
   ./gradlew clean
   ```
2. Sync Gradle files:
   ```bash
   ./gradlew --refresh-dependencies
   ```
3. Check Java version:
   ```bash
   java -version
   ```

### Firebase Configuration Issues
- Verify `google-services.json` is in the correct location (`app/` directory)
- Ensure the package name matches your Firebase console configuration
- Check that the Firebase plugin version in `build.gradle` is compatible

## Resources

- [Android Developers Official Documentation](https://developer.android.com/)
- [Firebase Documentation](https://firebase.google.com/docs/android/setup)
- [Android Gradle Plugin Documentation](https://developer.android.com/build)
- [Material Design Guidelines](https://m3.material.io/)

## Support

For issues and questions:
1. Check the troubleshooting section above
2. Review Android and Firebase documentation
3. Check build reports in `build/reports/`

## License

This project is provided as-is. Modify as needed for your use case.

## Version History

- **v1.0** - Initial release
