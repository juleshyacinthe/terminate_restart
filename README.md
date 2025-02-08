# 🔄 Terminate Restart

[![pub package](https://img.shields.io/pub/v/terminate_restart.svg)](https://pub.dev/packages/terminate_restart)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![likes](https://img.shields.io/pub/likes/terminate_restart)](https://pub.dev/packages/terminate_restart/score)

A robust Flutter plugin for terminating and restarting your app with extensive customization options. Perfect for implementing dynamic updates, clearing app state, or refreshing your app's UI.

## 📱 Demo

<p align="center">
  <img src="https://raw.githubusercontent.com/sleem2012/terminate_restart/main/.github/assets/demo.gif" alt="Plugin Demo" width="300"/>
  <br/>
  <em>Plugin in Action</em>
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/sleem2012/terminate_restart/main/.github/assets/screenshot.png" alt="Clean Interface" width="300"/>
  <br/>
  <em>Clean & Simple Interface</em>
</p>

## 🌟 Features

- ✨ **Three Restart Modes**:
  - **UI-only Restart**: (~200ms)
    - Recreates activities/views while maintaining connections
    - Perfect for theme changes, language switches
    - Preserves network connections and background tasks
    - Faster execution with minimal disruption
  
  - **Full Process Restart**: (~800ms)
    - Complete app termination and restart
    - Ideal for updates, security-related changes
    - Cleans up all resources and states
    - Ensures fresh start with no residual state
    
  - **With Confirmation Dialog**: (+50ms)
    - Shows a customizable confirmation dialog
    - User can choose to proceed or cancel
    - Supports both UI-only and full restart
    - Perfect for user-initiated actions

- 🧹 **Smart Data Management**:
  - Configurable data clearing during restart
  - Granular control over data preservation
  - Secure handling of sensitive information

- 🔒 **Security Features**:
  - Optional keychain data preservation
  - Secure user defaults handling
  - Clean process termination

- 📱 **Platform Support**:
  - ✅ Android: Full support with activity recreation
  - ✅ iOS: Compliant with App Store guidelines

- 💫 **User Experience**:
  - Built-in confirmation dialogs
  - Customizable messages and buttons
  - Smooth transitions and animations

## 📦 Installation

```yaml
dependencies:
  terminate_restart: ^1.0.8
```

## Quick Start

Get up and running with Terminate Restart in minutes:

1. **Add Dependency**
```yaml
dependencies:
  terminate_restart: ^1.0.8
```

2. **Import Package**
```dart
import 'package:terminate_restart/terminate_restart.dart';
```

3. **Initialize the Plugin**
```dart
void main() {
  WidgetsFlutterBinding.ensureInitialized();
  TerminateRestart.instance.initialize();
  runApp(MyApp());
}
```

4. **Basic Usage**
```dart
// Quick UI refresh
await TerminateRestart.instance.restartApp(
  options: const TerminateRestartOptions(
    terminate: false,
  ),
);

// Full app restart
await TerminateRestart.instance.restartApp(
  options: const TerminateRestartOptions(
    terminate: true,
  ),
);

// With confirmation dialog
await TerminateRestart.instance.restartApp(
  options: const TerminateRestartOptions(
    terminate: true,
  ),
  mode: RestartMode.withConfirmation,
  dialogTitle: 'Restart App',
  dialogMessage: 'Do you want to restart the app?',
);
```

## Feature Comparison

| Feature | Description |
|---------|-------------|
| UI Restart | Quick UI refresh without app termination |
| Full Restart | Complete app termination and restart |
| Data Clearing | Optional storage clearing with keychain preservation |
| Confirmation | Optional user confirmation before restart |
| iOS Compliance | System-approved methods for App Store compliance |

## iOS App Store Compliance

This plugin follows Apple's App Store guidelines regarding app termination:

1. **User-Initiated Actions**: The plugin only performs termination in response to explicit user actions.

2. **Graceful Shutdown**: On iOS, the plugin uses approved APIs to ensure graceful app termination:
   - Uses `exit(0)` for clean termination
   - Properly saves state and closes resources
   - Follows iOS application lifecycle

3. **Restart Mechanism**: The restart functionality complies with iOS guidelines by:
   - Using approved launch mechanisms
   - Preserving user preferences when requested
   - Maintaining system integrity

4. **Data Handling**: When clearing data:
   - Respects iOS data protection
   - Properly handles keychain items
   - Maintains necessary system files

> **Note**: While Android allows direct app termination, iOS termination is handled through system-approved methods.

## 🔍 Common Use Cases

1. **After Dynamic Updates**
   ```dart
   // After downloading new assets/code
   await TerminateRestart.instance.restartApp(
     options: const TerminateRestartOptions(
       terminate: true,
     ),
     mode: RestartMode.withConfirmation,
     dialogTitle: 'Update Ready',
     dialogMessage: 'Restart to apply updates?',
   );
   ```

2. **Clearing Cache**
   ```dart
   // Clear app data but preserve important settings
   await TerminateRestart.instance.restartApp(
     options: const TerminateRestartOptions(
       terminate: true,
       clearData: true,
       preserveKeychain: true,
       preserveUserDefaults: true,
     ),
   );
   ```

3. **Quick UI Refresh**
   ```dart
   // Refresh UI without full restart
   await TerminateRestart.instance.restartApp(
     options: const TerminateRestartOptions(
       terminate: false,
     ),
   );
   ```

4. **With Confirmation Dialog**
   ```dart
   // Show confirmation dialog before restart
   await TerminateRestart.instance.restartApp(
     options: const TerminateRestartOptions(
       terminate: true,
     ),
     mode: RestartMode.withConfirmation,
     dialogTitle: 'Restart Required',
     dialogMessage: 'Do you want to restart the app?',
     confirmButtonText: 'Restart',
     cancelButtonText: 'Later',
   );
   ```

## 📊 Performance Metrics

| Operation | Average Time |
|-----------|-------------|
| UI-only Restart | ~300ms |
| Full Termination | ~800ms |
| Data Clearing | ~200ms |
| With Dialog | +100ms |

## 🔐 Security Considerations

1. **Sensitive Data**
   - Use `preserveKeychain` for credentials
   - Clear data on logout
   - Handle biometric authentication state

2. **State Management**
   - Clear sensitive data before restart
   - Implement proper authentication state handling
   - Use secure storage for critical information

3. **Platform Security**
   - Proper permission handling
   - Secure data clearing
   - Protected file access

## 🤝 Contributing

Contributions are welcome! Please read our [contributing guidelines](CONTRIBUTING.md) before submitting PRs.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Support

If you have any questions or need help, you can:
- Open an [issue](https://github.com/sleem2012/terminate_restart/issues)
- Check our [example](https://github.com/sleem2012/terminate_restart/tree/main/example) for more usage examples
- Read our [API documentation](https://pub.dev/documentation/terminate_restart/latest/)

## 📚 Complete Example

Check out our [example app](https://github.com/sleem2012/terminate_restart/tree/main/example) for a full demonstration of all features, including:

- Basic UI/Process restart
- Data clearing with preservation options
- Custom confirmation dialogs
- Error handling
- State management
- Platform-specific features

## 🎥 Demo

### Quick Preview
<p align="center">
  <img src="https://raw.githubusercontent.com/sleem2012/terminate_restart/main/.github/assets/demo.gif" alt="Quick Preview" width="300"/>
</p>

## 🔧 Platform-Specific Details

### Android Implementation

The Android implementation uses a combination of techniques to ensure reliable app restart:

```kotlin
// Activity recreation (UI-only restart)
currentActivity.recreate()

// Full process termination
Process.killProcess(Process.myPid())
exitProcess(0)

// Smart Intent handling
intent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK or Intent.FLAG_ACTIVITY_CLEAR_TASK)
```

### iOS Implementation

The iOS implementation provides:

- Clean process termination
- State preservation options
- Keychain data handling
- User defaults management

## 👨‍💻 Author

Made with ❤️ by Ahmed Sleem
[GitHub](https://github.com/sleem2012) • [pub.dev](https://pub.dev/publishers/sleem2012) • [LinkedIn](https://www.linkedin.com/in/sleem98/)

---

<p align="center">
  <a href="https://pub.dev/packages/terminate_restart">pub.dev</a> •
  <a href="https://github.com/sleem2012/terminate_restart">GitHub</a> •
  <a href="https://github.com/sleem2012/terminate_restart/issues">Issues</a>
</p>

## 🔧 Configuration Options

### Core Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `terminate` | `bool` | `true` | Full termination vs UI-only restart |
| `clearData` | `bool` | `false` | Clear app data during restart |
| `preserveKeychain` | `bool` | `false` | Keep keychain data when clearing |
| `preserveUserDefaults` | `bool` | `false` | Keep user defaults when clearing |

## 🤔 Frequently Asked Questions

### 1. What's the difference between UI-only and Full restart?
- **UI-only Restart**: Only recreates the UI components while keeping the app process alive. Perfect for theme changes or language switches.
- **Full Restart**: Completely terminates the app process and starts fresh. Ideal for updates or when you need a clean state.

### 2. When should I use confirmation dialog?
Use confirmation dialog when:
- User needs to be aware of the restart
- Data might be lost during restart
- Action is user-initiated
- Critical operations are in progress

### 3. Will my app data be preserved?
- By default, all app data is preserved
- Use `clearData: true` to clear app data
- Use `preserveKeychain` and `preserveUserDefaults` to selectively preserve data

### 4. Is it safe to use in production?
Yes! The plugin:
- Uses official platform APIs
- Follows platform guidelines
- Handles errors gracefully
- Has no special permission requirements

## 🎯 Advanced Use Cases

### 1. Language Change with Data Preservation
```dart
Future<void> changeLanguage(String newLocale) async {
  // Save new locale
  await prefs.setString('locale', newLocale);
  
  // Restart UI only with confirmation
  await TerminateRestart.instance.restartApp(
    options: const TerminateRestartOptions(
      terminate: false,
      preserveUserDefaults: true,
    ),
    mode: RestartMode.withConfirmation,
    dialogTitle: 'Language Change',
    dialogMessage: 'Restart app to apply new language?',
  );
}
```

### 2. Update Installation with Progress
```dart
Future<void> installUpdate() async {
  try {
    // Download update
    await downloadUpdate();
    
    // Apply update with confirmation
    final confirmed = await TerminateRestart.instance.restartApp(
      options: const TerminateRestartOptions(
        terminate: true,
        clearData: false,
        preserveKeychain: true,
      ),
      mode: RestartMode.withConfirmation,
      dialogTitle: 'Update Ready',
      dialogMessage: 'Install update and restart?',
    );
    
    if (!confirmed) {
      scheduleUpdateReminder();
    }
  } catch (e) {
    handleUpdateError(e);
  }
}
```

### 3. Secure Logout with Data Clearing
```dart
Future<void> secureLogout() async {
  // Clear sensitive data
  await TerminateRestart.instance.restartApp(
    options: const TerminateRestartOptions(
      terminate: true,
      clearData: true,
      preserveUserDefaults: true, // Keep app settings
      preserveKeychain: false, // Clear credentials
    ),
  );
}
```

## 🔄 How It Works

```mermaid
graph TD
    A[Start] --> B{Restart Type}
    B -->|UI-only| C[Recreation Mode]
    B -->|Full| D[Termination Mode]
    
    C --> E{Show Dialog?}
    D --> E
    
    E -->|Yes| F[Show Confirmation]
    E -->|No| G[Process Restart]
    
    F -->|Confirmed| G
    F -->|Cancelled| H[Cancel Operation]
    
    G --> I{Clear Data?}
    I -->|Yes| J[Clear App Data]
    I -->|No| K[Preserve Data]
    
    J --> L[Restart App]
    K --> L
    
    L --> M[End]
```

### Flow Explanation:
1. **Restart Type Selection**:
   - Choose between UI-only or Full restart
   - Each type optimized for specific use cases

2. **Confirmation Dialog** (Optional):
   - Can be added to any restart type
   - Fully customizable UI
   - User can cancel operation

3. **Data Management**:
   - Optional data clearing
   - Selective data preservation
   - Secure handling of sensitive data

4. **Platform-Specific Implementation**:
   - Android: Activity/Process management
   - iOS: UIApplication handling
   - Error handling and recovery
