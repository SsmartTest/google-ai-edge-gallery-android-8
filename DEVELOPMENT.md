# Development notes

## Build app locally

To successfully build and run the application through Android Studio, you need to configure it with your own HuggingFace Developer Application ([official doc](https://huggingface.co/docs/hub/oauth#creating-an-oauth-app)). This is required for the model download functionality to work correctly.

After you've created a developer application:

1. In [`ProjectConfig.kt`](https://github.com/google-ai-edge/gallery/blob/main/Android/src/app/src/main/java/com/google/ai/edge/gallery/common/ProjectConfig.kt), replace the placeholders for `clientId` and `redirectUri` with the values from your HuggingFace developer application.

1. In [`app/build.gradle.kts`](https://github.com/google-ai-edge/gallery/blob/c1b50e160a66d5ea2ec2d8d8e63088b3cc0761bc/Android/src/app/build.gradle.kts#L41-L44), modify the `manifestPlaceholders["appAuthRedirectScheme"]` value to match the redirect URL you configured in your HuggingFace developer application.

## Build APK from Command Line

To build an APK without Android Studio:

### Option 1: Debug APK (for testing)
```bash
cd Android/src
./gradlew assembleDebug
```
Output: `app/build/outputs/apk/debug/app-debug.apk`

### Option 2: Release APK (for distribution)
```bash
cd Android/src
./gradlew assembleRelease
```
Output: `app/build/outputs/apk/release/app-release.apk`

### Building in GitHub Codespace
The Codespace environment has Java and Gradle pre-installed. To build the APK:

```bash
# Navigate to the Android project directory
cd Android/src

# Run the build command
./gradlew assembleDebug

# The APK will be generated in app/build/outputs/apk/debug/
```

**Note:** The first build will download the Android SDK and dependencies, which may take several minutes. Subsequent builds will be faster.

### Minimum Requirements
- Java 11+ (Java 25 is available in Codespace)
- 2GB RAM minimum
- Internet connection for downloading dependencies
