# Cyber Surfers
Cyber Surfers is a project for Bachelor's Diploma: 'Educational game about cybersecurity for primary school students' (Computer Science, AGH University of Krakow).

It's an educational mobile game designed to increase awareness and knowledge of cybersecurity risks among elementary school students.

The mobile application was developed using the Android Studio tool. The language used was Koltin and the Jetpack Compose framework. The server application was also written in Kotlin using the Ktor framework.

The result of the work is a server application running in a program with a simple and user-friendly interface, and an Android-based mobile application capable of connecting to the server application via network communication in a local area network.

## Gameplay
[![Cyber Surfers | Gameplay](/assets/CyberSurfers-gameplay-thumbnail.png)](https://www.youtube.com/watch?v=BA9oQ8lpuAE)

## Server App (Backend) repository
[Nepommuck/**CyberSurfers-Backend**](https://github.com/Nepommuck/CyberSurfers-Backend)

## CyberSurfers-Frontend - Mobile App (Client)

### App config
App config can be changed by editing the
**[`AppConfig.kt`](app/src/main/java/edu/agh/susgame/front/config/AppConfig.kt) file**

#### Local (Mock) setup
Set the following in the
**[`AppConfig.kt`](app/src/main/java/edu/agh/susgame/front/config/AppConfig.kt) file**:
```kotlin
override val providers = ProviderType.MockLocal
```
The remaining configuration will be ignored

#### Server setup
1. Run the server ([**CyberSurfers-Backend** repository](https://github.com/Nepommuck/CyberSurfers-Backend)) in the same network
2. Get your public IPv4 address. On Linux / macOS it can be achieved by:
    ```
    ❯ ip addr | grep "inet "
    inet 127.0.0.1/8
    inet 192.168.0.100/24 brd 192.168.0.255
    ```
   where `192.168.0.100` is what interests us
3. Update the **[`AppConfig.kt`](app/src/main/java/edu/agh/susgame/front/config/AppConfig.kt) file**:
    ```kotlin
    override val providers = ProviderType.Web

    override val webConfig = AppConfig.WebConfig(
        // ...
        defaultIpAddress = "192.168.0.15",
        // ...
    )
    ```
    Setting the `defaultIpAddress` is optional, but will make it unnecessary to provide the IP every
    this the app is run.

### Working with DTO
- In order to modify DTO, commit to [**CyberSurfers-DTO** repository](https://github.com/Nepommuck/CyberSurfers-DTO)
- In order to update DTO to newest version, run [**`update-DTO.sh`**](./scripts/update-DTO.sh) script
- In order to update DTO to given **CyberSurfers-DTO** repository branch, run [**`update-DTO.sh`**](./scripts/update-DTO.sh) script with branch name as an argument
