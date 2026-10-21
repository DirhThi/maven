# maven

Kho Maven public chứa các thư viện Android đã build sẵn (`.aar`) và Gradle plugin đi kèm.
Nội dung được sinh tự động bởi script publish từ repo nguồn (private), đừng sửa tay.

Đọc qua GitHub Pages, không cần đăng nhập: `https://dirhthi.github.io/maven`

| Thư viện | Coordinate |
|---|---|
| Ads | `dev.ndt.kit:ads` ([metadata](dev/ndt/kit/ads/maven-metadata.xml)) |
| Core | `dev.ndt.kit:core` ([metadata](dev/ndt/kit/core/maven-metadata.xml)) |
| Plugin mã hoá `ads_config` | id `dev.ndt.kit.ads` |

## Cách dùng

`settings.gradle.kts`

```kotlin
pluginManagement {
    repositories {
        google()
        mavenCentral()
        gradlePluginPortal()
        maven("https://dirhthi.github.io/maven")
    }
}
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven("https://dirhthi.github.io/maven")
        maven("https://jitpack.io")
        maven("https://android-sdk.is.com/")
    }
}
```

`app/build.gradle.kts`

```kotlin
plugins {
    id("com.android.application")
    id("dev.ndt.kit.ads") version "<version>"
}

dependencies {
    implementation("dev.ndt.kit:ads:<version>")
}
```

Đặt `ads_config.json` ở `app/config/ads_config.json`; plugin tự mã hoá thành `assets/ads_config.dat` lúc build.
