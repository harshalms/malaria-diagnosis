# Documentation for Android application developement

This document guides you through the process of converting a YOLOv7-Tiny Torch model to TensorFlow Lite (TFLite) for malria detection/diagnostics on Android devices developed using Flutter and Dart. The conversion process involves several steps, leveraging different libraries and tools to ensure compatibility across various frameworks. This guide assumes familiarity with Python and the command line. It also provides instructions on setting up your development environment on a Windows machine.

## Table of Contents

1. [Converting YOLOv7-Tiny Torch Model to TFLite](#converting-yolov7-tiny-torch-model-to-tflite)
2. [Setting Up Flutter and Dart Environment](#setting-up-flutter-and-dart-environment)
3. [Basic Structure of the Documentation](#basic-structure-of-the-documentation)

## 1. Converting YOLOv7-Tiny Torch Model to TFLite

To convert the YOLOv7-Tiny Torch model (`yolov7-tiny.pt`) to a TensorFlow Lite model (`yolov7-tiny.tflite`), follow these steps:

1. **Install the required packages**:
   ```bash
   !pip install --upgrade setuptools pip --user
   !pip install onnx
   !pip install onnxruntime
   !pip install onnxruntime
   !pip install protobuf<4.21.3
   !pip install onnxruntime-gpu
   !pip install onnx>=1.9.0
   !pip install onnx-simplifier>=0.3.6 --user
   ```

1. **Install PyTorch and TensorFlow**: Ensure you have both `PyTorch` and `TensorFlow` installed in your Python environment. You can install them using pip

2. **Converting PyTorch Model to ONNX Graph**: The YOLOv7 source code includes a script for converting the PyTorch model to an ONNX graph. This process is crucial for ensuring that the model can be utilized across different deep learning frameworks.


3. **Converting ONNX Graph to TensorFlow Model**:  Use the `onnx-tensorflow` library to convert the ONNX graph to a TensorFlow model. This step is necessary for further conversion to TensorFlow Lite.

3. Converting TensorFlow Model to TensorFlow Lite: Finally, convert the TensorFlow model to TensorFlow Lite using the official TensorFlow Python library.

## 2. Setting Up Flutter and Dart Environment

To develop Android applications using Flutter and Dart on a Windows machine, follow these steps:

1. **Install Flutter SDK**: Download the latest stable version of the Flutter SDK from the [official Flutter website](https://flutter.dev/docs/get-started/install/windows). Follow the installation instructions provided.

2. **Set Up Environment Variables**: Add the Flutter SDK to your PATH environment variable. This allows you to run Flutter commands from any directory in the command prompt.

3. **Install Dart**: The Dart SDK comes bundled with the Flutter SDK. Ensure that the Flutter installation process has completed successfully, as this will also set up Dart.

4. **Install Android Studio**: Download and install Android Studio from the [official Android Studio website](https://developer.android.com/studio). This IDE provides the necessary tools for Android development, including the Android SDK and emulator.

5. **Configure Android Studio**: Open Android Studio and configure it to work with Flutter by following the prompts during the initial setup.

6. **Run Flutter Doctor**: Open a terminal or command prompt and run `flutter doctor`. This command checks your environment and displays a report of the status of your Flutter installation. Fix any issues reported by running the suggested commands.

## 3. Android App Documentation

1. **Create a project**: 
```bash
flutter create <project_name>
```
2. **Directory Structure**:

```bash
<project_name>/
├── android/
│   ├── app/
│   │   ├── src/
│   │   │   ├── main/
│   │   │   │   ├── AndroidManifest.xml
│   │   │   │   ├── java/
│   │   │   │   │   └── com/
│   │   │   │   │       └── example/
│   │   │   │   │           └── <project_name>/
│   │   │   │   │               └── MainActivity.java
│   │   │   │   └── res/
│   │   │   │       ├── drawable/
│   │   │   │       ├── mipmap/
│   │   │   │       ├── layout/
│   │   │   │       └── values/
│   │   └── build.gradle
│   ├── build.gradle
│   └── gradle/
│       └── wrapper/
│           ├── gradle-wrapper.jar
│           └── gradle-wrapper.properties
├── ios/
│   ├── Runner/
│   │   ├── AppDelegate.swift
│   │   ├── Assets.xcassets/
│   │   ├── Base.lproj/
│   │   ├── Info.plist
│   │   └── Runner.xcodeproj/
│   └── Podfile
├── lib/
│   ├── main.dart
├── test/
│   ├── widget_test.dart
├── .gitignore
├── .metadata
├── .packages
├── .flutter-plugins
├── pubspec.yaml
└── README.md
```

- **android**: Contains the Android-specific code and configuration files.
  - **app**: Contains the main Android application module.
  - **build**: Automatically generated build files.
  - **gradle**: Contains Gradle wrapper files.
- **ios**: Contains the iOS-specific code and configuration files.
  - **Runner**: Contains the main iOS application module.
  - **Podfile**: Specifies the iOS dependencies.
- **lib**: Contains the Dart source code for your Flutter application.
  - **main.dart**: The entry point of your Flutter application.
  - **controller**: Camera functionality
  - **res**: Resources for color & app values like padding, margin, border etc.
  - **services**: Sign up & login functionality, firebase authetication, Camera permission
  - **tensorflow**: Model inference and bounding box visualization functionality
  - **theme**: App theme, buttons style etc.
  - **utils**: Constant texts, fonts style, Login details data type validation
  - **views**: Login screen, welcome screen, camera view screen, image uploader screen, result screen
  - **widgets**: Buttons and dialogues
- **test**: Contains the unit tests for your Flutter application.
- **.gitignore**: Specifies intentionally untracked files to ignore when using Git.
- **.metadata**: Stores metadata about the project.
- **.packages**: Specifies the Dart package dependencies for the project.
- **pubspec.yaml**: Defines the Flutter project dependencies and metadata.


### Running Code in Android Emulator

#### Using Android Studio:

1. **Open Android Studio**: Launch Android Studio on your computer.

2. **Open Project**: Open the Flutter project in Android Studio.

3. **Start Android Emulator**: 
   - If you haven't already, create or open an Android emulator through AVD Manager.
   - Click on the AVD Manager icon in the toolbar.
   - Select the desired emulator from the list and click "Launch" or "Play" button.

4. **Run Code**: 
   - Ensure the emulator is running.
   - Click the "Run" button (green arrow) in the Android Studio toolbar.
   - Choose the emulator device from the dropdown if multiple devices are available.
   - Wait for the build process to complete and the app to be installed on the emulator.
   - The app should automatically launch on the emulator.

#### Using Command Line:

1. **Navigate to Project Directory**: Open your terminal or command prompt and navigate to the directory of your Flutter project.

2. **Start Android Emulator**: 
   - Ensure that the Android emulator is running or start it using AVD Manager or command line tools like `emulator`.

3. **Run Code**: 
   - Execute the following command in the terminal:
     ```
     flutter run
     ```
   - This command will build the Flutter project and install it on the running emulator.
   - The app should automatically launch on the emulator.

#### NOTE:
- Make sure that your Flutter project is properly configured and all dependencies are installed before running the code.
- It may take some time for the emulator to start and for the app to be installed, especially on first run or after updates.
- Emulator uses good amount of memory to run seamlessly. If your application crashes then you need to close other program using memory


### Creating an APK File for Flutter Project

1. **Navigate to Project Directory**: Open your terminal or command prompt and navigate to the directory of your Flutter project.

2. **Build APK**: Execute the following command to build the APK file:
   ```bash
   1. flutter build apk
      OR
   2. flutter build apk --split-per-abi
   ```

#### NOTE: 
- `flutter build apk --split-per-abi` command creates the compressed or light weight APK.
----------------------------
Developed by:
- [Harshal Shedolkar BT18M014](bt18m014@smail.com)

Research Advisor:
- [Nirav P Bhatt](niravbhatt@smail.iitm.ac.in)
