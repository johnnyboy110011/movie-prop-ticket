# Movie Prop Ticket for Android

An offline, fullscreen portrait movie prop powered by the supplied `ticket.html`.
Double-tap the ticket to open a hidden editor. Change scrolling text, prop labels,
ticket number, date/time label, scripted starting date/time, and bottom text; tap Save.
Edits persist on the device using Android WebView DOM storage.

## IMPORTANT: Upload with original folders intact

The Android module MUST remain in `app/` and the workflow MUST remain in
`.github/workflows/`. Uploading all files from separate folders into the root
will cause GitHub Actions to fail (`assembleDebug` task not found).

**Recommended: GitHub Desktop (Windows)**

1. Create a NEW EMPTY PRIVATE repository on GitHub. Do not add a README there.
2. Download and unzip this archive on your computer.
3. In GitHub Desktop, select File > Add local repository > Choose the extracted folder.
   If prompted that it is not a Git repository, choose 'create a repository here'.
4. Commit the files, then choose Publish repository and make it private. Alternatively
   clone the empty repository into a folder and copy the extracted files into its root,
   then commit and push in GitHub Desktop.
5. In GitHub, open Actions > Build Android APK > Run workflow (the first push may
   have started it already).
6. Once successful, open the run's Artifacts section; download
   `movie-prop-ticket-apk`, unzip it, then install `app-debug.apk` on Android.

**Alternative: Git command line**
After creating a new empty repo at `https://github.com/USERNAME/REPO`:
```bash
cd PATH_TO_EXTRACTED_FOLDER
git init
git branch -M main
git add .
git commit -m "Initial Android movie prop"
git remote add origin https://github.com/USERNAME/REPO.git
git push -u origin main
```

## Folder checklist

- `.github/workflows/build-apk.yml`
- `app/build.gradle`
- `app/src/main/AndroidManifest.xml`
- `app/src/main/assets/ticket.html`
- `app/src/main/java/com/movieprop/ticket/MainActivity.java`
- `build.gradle` (root)
- `settings.gradle` (root)
- `gradle.properties` (root)

## Details

- Java 17, Gradle 8.10.2, Android Gradle Plugin 8.7.3, compile SDK 35
- Android API 23+; offline WebView app, no network permission
- Screen stays on, fullscreen portrait, script-controlled countdown
- The HTML originally fetched Google Fonts over the network; the app uses
  system fallback fonts so it is independent of internet access.
- GitHub Actions produces a debug-signed APK suitable for filming/testing,
  not a Play Store production release.
- Fictional movie prop. Not a valid transit fare.
