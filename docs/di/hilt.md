# Hilt

**Категория:** Dependency Injection
**Официальная документация:** [developer.android.com/training/dependency-injection/hilt-android](https://developer.android.com/training/dependency-injection/hilt-android)

Краткое описание того, что делает библиотека.

## 1. Добавление зависимостей в `libs.versions.toml`

```toml
[versions]
hilt = "2.51.1" 

[libraries]
hilt-android = { group = "com.google.dagger", name = "hilt-android", version.ref = "hilt" }
hilt-compiler = { group = "com.google.dagger", name = "hilt-android-compiler", version.ref = "hilt" }

[plugins]
hilt-android = { id = "com.google.dagger.hilt.android", version.ref = "hilt" }
```

## 2. Применение плагинов

**Проектный `build.gradle.kts`:**
```kotlin
plugins {
    alias(libs.plugins.hilt.android) apply false
}
```

**Модульный `build.gradle.kts`:**
```kotlin
plugins {
    alias(libs.plugins.hilt.android)
    id("kotlin-kapt")
}

dependencies {
    implementation(libs.hilt.android)
    kapt(libs.hilt.compiler)
}
```

## 3. Настройка в коде

Аннотируй класс `Application` и зарегистрируй его в манифесте.
```kotlin
@HiltAndroidApp
class MyApplication : Application()
```
```xml
<application
    android:name=".MyApplication" ... >
```
**Примечание:** Активности и фрагменты, использующие Hilt, должны быть аннотированы `@AndroidEntryPoint`.
