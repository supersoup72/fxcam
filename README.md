# FX Cam — Build Instructions (GitHub Codespaces)

## Step 1: Push this project to GitHub
1. Go to github.com on your phone → New repository → name it "fxcam" → Create
2. Open GitHub Codespaces from that repo (green Code button → Codespaces → Create)

## Step 2: Inside Codespaces terminal, install Android SDK
```bash
# Install Java
sudo apt-get update && sudo apt-get install -y openjdk-17-jdk wget unzip

# Download Android command line tools
mkdir -p ~/android-sdk/cmdline-tools
cd ~/android-sdk/cmdline-tools
wget https://dl.google.com/android/repository/commandlinetools-linux-11076708_latest.zip
unzip commandlinetools-linux-*.zip
mv cmdline-tools latest

# Set environment
export ANDROID_HOME=~/android-sdk
export PATH=$PATH:$ANDROID_HOME/cmdline-tools/latest/bin:$ANDROID_HOME/platform-tools

# Accept licenses and install SDK
yes | sdkmanager --licenses
sdkmanager "platforms;android-34" "build-tools;34.0.0" "platform-tools" "ndk;26.1.10909125" "cmake;3.22.1"
```

## Step 3: Build the APK
```bash
cd /workspaces/fxcam
chmod +x gradlew
./gradlew assembleDebug
```

First build: ~5-10 minutes on Codespaces servers.
APK will be at: `app/build/outputs/apk/debug/app-debug.apk`

## Step 4: Install on your S20 FE
1. In Codespaces file explorer → navigate to `app/build/outputs/apk/debug/`
2. Right-click `app-debug.apk` → Download
3. On your phone: open Downloads → tap the APK → Install
4. If blocked: Settings → Apps → Special app access → Install unknown apps → Chrome → Allow

## Rebuilding after changes
```bash
./gradlew assembleDebug
# Takes ~1-2 min after first build
```

## Effects in the app
- Hue Shift, V-Wiggle, H-Wiggle, V-Wave, H-Wave
- Swirl, Fisheye, Ripple, Fractal
- God Rays, Glow
- Organic Wiggle, CRT Beam
- Custom GLSL (tap Custom chip → opens editor)

## Controls
- TAP chip → select (shows sliders)
- LONG PRESS chip → toggle on/off (green dot = active)
- DRAG ≡ handle → reorder effects
- Multiple effects stack in order shown
