
# GlobalExceptionHandler

![header](https://github.com/Alonew0lfxx/GlobalExceptionHandler/blob/c56bf46d4497edb24425896abf680cc3155a7579/assets/header.png?raw=true)

Rather than showing the default boring system error dialog, it serves to open the
desired Activity whenever the Application crashes. And it has only 2 functions


## Installation

Step 1. Add the JitPack repository to your settings.gradle file

```gradle
pluginManagement {
    repositories {
        gradlePluginPortal()
        google()
        mavenCentral()
        maven { url 'https://jitpack.io' } // Add this line

    }
}
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
        maven { url 'https://jitpack.io' } // Add this line
    }
}
```

Step 2. Add The GlobalExceptionHandler Dependency to your build.gradle(app) file.

```gradle
dependencies {
    implementation 'com.github.Alonew0lfxx:GlobalExceptionHandler:1.0.0'
}
```

## Usage/Examples

App.kt
```kotlin
class App : Application() {
    override fun onCreate() {
        super.onCreate()
        GlobalExceptionHandler.initialize(this,CrashActivity::class.java)
    }
}
```

CrashActivity.kt
```kotlin
class CrashActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        GlobalExceptionHandler.getThrowableFromIntent(intent).let { throwable ->
            // Report the crash error to your servers or etc...
        }
        setContentView(view)
    }
```


## Functions

#### Initalize the GlobalExceptionHandler

```kotlin
  GlobalExceptionHandler.initalize(applicationContext, activityToBeLaunched)
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `applicationContext` | `Context` | Required to launch Intent |
| `activityToBeLaunched` | `Activity` | The activity to be launched whenerver app crashes |

#### Get Throwable from Intent

```kotlin
  GlobalExceptionHandler.getThrowableFromIntent(intent): Throwable?
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `intent`  | `Intent` | Retrives crash data from intent. It should be called inside of the **activityToBeLaunched** Activity. |

## Screenshots
With GlobalExceptionHandler | Without GlobalExceptionHandler
--- | ---
![](https://github.com/Alonew0lfxx/GlobalExceptionHandler/blob/master/assets/gif1.gif?raw=true) | ![](https://github.com/Alonew0lfxx/GlobalExceptionHandler/blob/master/assets/gif0.gif?raw=true)

###### Emirhan Kolver © 2022 | 24.09.2022
