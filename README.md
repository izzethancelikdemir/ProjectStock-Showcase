#  📦 Project Stock - B2B Inventory Management Solution
> **Note:** As this project is being prepared for commercial release, the source code is kept in a **Private Repository**. This showcase repository demonstrates the project's tech stack, architecture, and capabilities.

 ## 📱 About the Project
 **Project Stock** is a comprehensive **B2B Android Application** designed for businesses to manage inventory, personnel, orders, and warehouse counting processes from a single platform *(also a supplier module is work in progress for now)*. It is built with modern Android development standards, ensuring scalability *(tablet and phone layouts)* and testability.

---

 ## 🎥 Some futuristic features in Project Stock app
 
 ## **Stock Island**
 
 Stock Island is an in-app notch which is the TopBar of the app.
 
 Here are some demo shows about Stock Island took in-app:
 
 * [TaskScreen ToolBar Mode *(short video)*](https://imgur.com/tOiJvTG) 
 * [Expanded or Compact Mode *(short video)*](https://imgur.com/5VdgaGe) 
 * [Notification Mode *(screenshot)*](https://imgur.com/1UQkpLd) 
 * [StockMovement Succeeded Mode *(screenshot)*](https://imgur.com/HASP7vs) 
 * [No Internet Connection Mode *(screenshot)*](https://imgur.com/PJDRYPs) 

---

 ## **Segmented Controllable Nav Bar**

NavBar in Project Stock is also acts like a notch and users both swipe or touch to navigate within app's main navigation routes.

Here is a demo show for this feature which took in-app:

* [NavBar demo show](https://imgur.com/ogI8Fa2) 

---
 
 ## **Product Management Flow with Barcode UI**
 
 Users can use Barcodes for add new products, count inventories etc.
 
 Here is the demo shows of this flow took in-app:
 
 * [Barcode UI's ProductFound and ProductScanning state in Tablet Layout *(for wide screens)*](https://imgur.com/nTevw5I)
 * [Barcode UI's TaskSelection state *(Inventory Count Tasks found related with product)* and Inventory Count state in Tablet Layout *(for wide screens)*](https://imgur.com/htQdrDF)
 * [Barcode UI's alert to user for a possible miss-touch interrupt *(by user)* happen while Inventory Count state in Tablet Layout *(for wide screens)*](https://imgur.com/g655YO4) 
 * [Barcode UI's ProductNotFound state in Tablet Layout *(for wide screens)*](https://imgur.com/4lp84HL)
 * [Barcode UI's AddNewProduct state after ProductNotFound state in Tablet Layout *(for wide screens)*](https://imgur.com/urYOiK9) 
 
---
 
## **Modular Role-based Management Flow**
 
 Management, My Tasks and My Business screens for different roles with different states of one screen.
 
 Here are the demo shows of this flow took in-app:
 
* [Management screen in Task Mode for Personnel Manager in Phone Layout *(for compact screens)*](https://imgur.com/OOzLpp2)   
* [My Business screen for Owner in Phone Layout *(for compact screens)*](https://imgur.com/IpN66pV) 
* [My Business screen for Owner in Tablet Layout *(for wide screens)*](https://imgur.com/qbjD8Vq) 
* [Tasks screen for Staff in Phone Layout *(for compact screens)*](https://imgur.com/5u5Y5l1) 
* [Tasks screen for Staff in Tablet Layout on light mode *(for wide screens)*](https://imgur.com/4ramgtJ) 
 
---
 
 ## **Other Features**
 
 And also more is featured in Project Stock.
 
 Here are the demo shows took in-app:
 
* [Compact search header in Products Screen for Phone Layout *(for compact screens)*](https://imgur.com/hH4qKxL) 
* [Light and Dark Mode switch in-app with preview cards in Phone Layout *(for compact screens)*](https://imgur.com/Ro4gNnb)

---

## 🛠 Tech Stack

Built with industry-standard modern libraries and tools:

* **Language:** 100% [Kotlin](https://kotlinlang.org/)
* **UI Framework:** [Jetpack Compose](https://developer.android.com/jetpack/compose) *(Material3 Design System)*
* **Architecture:** Clean Architecture *(MVVM + Repository Pattern)*
* **Dependency Injection:** [Hilt *(Dagger)*](https://dagger.dev/hilt/)
* **Concurrency:** Coroutines & Flow
* **Network:** [Retrofit](https://square.github.io/retrofit/) & OkHttp & Gson
* **Local Database:** [Room Database](https://developer.android.com/training/data-storage/room) *(Offline-first approach)*
* **Navigation:** Jetpack Navigation Compose
* **Key Libraries:**
    * **ML Kit:** For high-speed Barcode & QR code scanning.
    * **CameraX:** In-app camera handling.
    * **Coil:** Asynchronous image loading.
    * **DataStore:** Type-safe data storage for user preferences.
    * **Accompanist:** Permission handling.
    * **Kotlinx Serialization:** JSON serialization.

---

## 🏗 Architecture

The application follows **Clean Architecture** principles to ensure separation of concerns and testability:

1.  **Presentation Layer *(UI)*:**
    * Uses `ViewModel` to manage UI state via `StateFlow`.
    * Composable functions are responsible solely for UI rendering.
2.  **Domain Layer:**
    * Pure Kotlin code, independent of the Android framework.
    * Encapsulates business logic in `UseCase` classes *(e.g., `GetStockMovementsUseCase`)*.
3.  **Data Layer:**
    * Implements the `Repository` pattern *(`StockRepositoryImpl`)*.
    * Manages data sources *(Local Room DB vs. Remote API)* acting as the **Single Source of Truth**.
    * Handles network connectivity states via `ConnectivityObserver`.

---

### 🧩 Code Snippets

**1. Dependency Injection *(Hilt Module)*:**
```kotlin
@Module
@InstallIn(SingletonComponent::class)
abstract class AppModule {
    @Binds
    @Singleton
    abstract fun bindConnectivityObserver(
        networkConnectivityObserver: NetworkConnectivityObserver
    ): ConnectivityObserver
}
```
**2. UseCase Implementation *(Business Module)*:**
```kotlin
class GetStockMovementsUseCase @Inject constructor(
    private val stockRepository: StockRepository
) {
    operator fun invoke(page: Int, size: Int, ...): Flow<Resource<List<StockMovement>>> = flow {
        emit(Resource.Loading())
        try {
            val result = stockRepository.getStockMovements(page, size, ...)
            emit(result)
        } catch (e: Exception) {
            emit(Resource.Error(AppError.UnknownError(e.message)))
        }
    }
}
```
---
# ✨Key Features

* **Advanced Inventory Management:** Product entry, barcode lookup, stock movement tracking.

* **Role-Based Access Control:** Manage personnel permissions and roles.

* **Task Assignment System:** Assign and track counting or control tasks for staff.

* **ML Kit Integration:** Rapid and accurate barcode scanning via camera.

* **Reporting:** Detailed filtering for stock history and movements.

* **Dark Mode:** Fully supported dark/light theme adaptation.
---
---

# 👨‍💻 Contact

I am available to discuss the technical architecture and development process of this project.

* **LinkedIn:** [İzzet Han ÇELİKDEMİR](https://www.linkedin.com/in/izzet-han-çelikdemir-157184309)
* **Email:** [ihancelikdemir@gmail.com](mailto:ihancelikdemir@gmail.com)

---



