# Retrofit + OkHttp + Moshi

**Категория:** Сеть
**Официальная документация:** [square.github.io/retrofit/](https://square.github.io/retrofit/)

Связка для выполнения сетевых запросов.

## 1. Добавление зависимостей в `libs.versions.toml`

```toml
[versions]
retrofit = "2.9.0"
okhttp = "4.12.0"
moshi = "1.15.0"

[libraries]
retrofit-core = { group = "com.squareup.retrofit2", name = "retrofit", version.ref = "retrofit" }
retrofit-converter-moshi = { group = "com.squareup.retrofit2", name = "converter-moshi", version.ref = "retrofit" }
okhttp-logging-interceptor = { group = "com.squareup.okhttp3", name = "logging-interceptor", version.ref = "okhttp" }
moshi-core = { group = "com.squareup.moshi", name = "moshi", version.ref = "moshi" }
moshi-codegen = { group = "com.squareup.moshi", name = "moshi-kotlin-codegen", version.ref = "moshi" }
```

## 2. Подключение зависимостей

**Модульный `build.gradle.kts`:**
```kotlin
plugins {
    id("kotlin-kapt")
}

dependencies {
    implementation(libs.retrofit.core)
    implementation(libs.retrofit.converter.moshi)
    implementation(libs.okhttp.logging.interceptor)
    implementation(libs.moshi.core)
    kapt(libs.moshi.codegen)
}
```

## 3. Настройка в коде (Пример с Hilt)
```kotlin
@Module
@InstallIn(SingletonComponent::class)
object NetworkModule {
    // ...
}
```
**Примечание:** Не забудь `<uses-permission android:name="android.permission.INTERNET" />`.
