# Survive Game

## Work Process Overview

### Initial Setup

#### Decompile the APK
- Utilized online decompilation tools to convert the APK file into readable source code and resources.

#### Review Decompiled Code
- Analyzed the decompiled Java files and resource files to understand the structure and logic of the application.

### Key Components for Reverse Engineering

#### Manifest File
- **AndroidManifest.xml**: Contains crucial information about the app, such as components, permissions, and configurations.

#### Source Code
- **Java Files**: Located in the sources directory, these files contain the application's logic. Focus on the main activity and other significant activities or fragments related to gameplay.
- Identify files related to user input (ID entry) and the game logic.

#### Resources
- **res Directory**: Contains layouts, images, strings, and other resources used by the application.
  - **res/layout**: XML layout files defining UI components.
  - **res/drawable**: Images and other drawable resources.
  - **res/values**: XML files defining strings, colors, and styles.

### AndroidManifest.xml Key Points

- **Package Name**: `com.example.apk_decompile_project`
- **SDK Versions**:
  - `minSdkVersion`: 24
  - `targetSdkVersion`: 30
- **Permissions**: Requests internet permission (`android.permission.INTERNET`).
- **Activities**:
  - `com.classy.survivegame.Activity_Game`: Likely contains the main gameplay logic and user interface, set to portrait orientation.
  - `com.classy.survivegame.Activity_Menu`: Entry point of the application (launcher activity), also set to portrait orientation.

### Next Steps

#### Examine Activity_Menu
- This activity should handle the ID input when the game starts.

#### Examine Activity_Game
- This activity contains the game logic and user interactions.

#### Inspect Resources
- **res/layout**: Layout files defining the UI components.
- **res/values**: Strings, colors, and styles.

### Identifying and Fixing Bugs

#### Activity_Game.java

##### Update Toast Messages
Change:
```java
Toast.makeText(this, "Survived in " + state, 1).show();
} else {
Toast.makeText(this, "You Failed ", 1).show();
```java

To:
```java
Toast.makeText(this, "Survived in " + state, Toast.LENGTH_SHORT).show();
} else {
Toast.makeText(this, "You Failed ", Toast.LENGTH_SHORT).show();
