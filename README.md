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
```
To:
```java
Toast.makeText(this, "Survived in " + state, Toast.LENGTH_SHORT).show();
} else {
Toast.makeText(this, "You Failed ", Toast.LENGTH_SHORT).show();
```

##### Update Integer Parsing
Change:
```java
iArr[i] = Integer.valueOf(String.valueOf(id.charAt(i))).intValue() % 4;
```
To:
```java
iArr[i] = Integer.parseInt(String.valueOf(id.charAt(i))) % 4;
```

##### Update Integer Parsing
Change:
```java
<string name="url">https://pastebin.com/raw/‌‌‌T67TVJG9</string>
```
To:
```java
<string name="url">https://pastebin.com/raw/T67TVJG9</string>
```
### Testing and Validation
- Ran the application on an emulator or device to test the changes.
- Ensured the game logic works as expected and the correct toast message is displayed upon successful completion.

### Example ID and Steps

#### Enter a Valid ID
Example ID: `123456789`

#### Derived Steps
The steps array will be derived as follows:
- Character at index 0 ('1') -> 1 % 4 = 1 (Right)
- Character at index 1 ('2') -> 2 % 4 = 2 (Up)
- Character at index 2 ('3') -> 3 % 4 = 3 (Down)
- Character at index 3 ('4') -> 4 % 4 = 0 (Left)
- Character at index 4 ('5') -> 5 % 4 = 1 (Right)
- Character at index 5 ('6') -> 6 % 4 = 2 (Up)
- Character at index 6 ('7') -> 7 % 4 = 3 (Down)
- Character at index 7 ('8') -> 8 % 4 = 0 (Left)
- Character at index 8 ('9') -> 9 % 4 = 1 (Right)

#### Follow the Steps
- Press the buttons in the correct order as derived from the ID.

### Video Demonstration


https://github.com/Roei2606/APK_Decompile_Project_/assets/159260552/28b3c088-cb93-4f2e-ad8e-3810346fdb04



