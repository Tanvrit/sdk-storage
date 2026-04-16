# tanvrit-sdk · storage

> Hybrid SQLite + in-memory cache layer for offline-first data persistence across all KMP targets.

[![Maven](https://img.shields.io/badge/maven.tanvrit.com-1.0.12-blue)](https://maven.tanvrit.com)
![KMP](https://img.shields.io/badge/Kotlin_Multiplatform-8_targets-blueviolet)

## Install

### Option A — Tanvrit Gradle plugin _(recommended)_

```kotlin
// settings.gradle.kts
pluginManagement {
    repositories { maven { url = uri("https://maven.tanvrit.com") } }
}
```

```kotlin
// build.gradle.kts
plugins { id("com.tanvrit.sdk") version "1.0.12" }

tanvrit {
    version = "1.0.12"
    modules = listOf("storage")
}
```

### Option B — Direct dependency

```kotlin
// settings.gradle.kts
dependencyResolutionManagement {
    repositories { maven { url = uri("https://maven.tanvrit.com") } }
}
```

```kotlin
// build.gradle.kts  (KMP)
kotlin {
    sourceSets {
        commonMain.dependencies {
            implementation("com.tanvrit:storage:1.0.12")
        }
    }
}
```

## Targets

| Platform | Artifact |
|----------|----------|
| Android | `storage-android` |
| Iosarm64 | `storage-iosarm64` |
| Iossimulatorarm64 | `storage-iossimulatorarm64` |
| Iosx64 | `storage-iosx64` |
| Jvm | `storage-jvm` |
| Js | `storage-js` |
| Wasm Js | `storage-wasm-js` |
| Linuxx64 | `storage-linuxx64` |

## Quick start

```kotlin
// Tables extend DatabaseTable<T> for typed read/write
class ProductTable : DatabaseTable<Product>("products") {
    suspend fun saveProduct(p: Product) = store(p)
    suspend fun getProduct(id: String): Product? = loadById(id)
    suspend fun allProducts(): List<Product> = loadAll()
}
```

## Resources

- **Full SDK source:** [tanvrit/sdk](https://github.com/tanvrit/sdk)
- **All modules:** [maven.tanvrit.com](https://maven.tanvrit.com)
- **Issues:** [tanvrit/sdk/issues](https://github.com/tanvrit/sdk/issues)
