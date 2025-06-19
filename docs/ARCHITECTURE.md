# Architecture Overview

```
+------------------------------+
|          Android App        |
+------------------------------+
|  Presentation (UI) Layer     |
|  • Activities / Fragments    |
|  • ViewModels (MVVM)         |
|  • LiveData / StateFlow      |
+------------------------------+
|  Domain Layer                |
|  • Use-cases (business logic)|
+------------------------------+
|  Data Layer                  |
|  • Repositories              |
|  • Local (Room/Prefs)        |
|  • Remote (future API)       |
+------------------------------+
```

* **Clean Architecture / MVVM** – keeps code modular and testable.
* **DI** – Dagger/Hilt (future) for dependency injection.
* **Maps** – Google Maps SDK with KML/GeoJSON overlay utilities.
