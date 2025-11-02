# ✅ To Do List App – Jetpack Compose + Room + SharedPreferences

Implementação da camada de persistência para o App To Do List (atividade Soluções Mobile - UNISATC).

---

## 🎯 Objetivo
Implementar a persistência dos dados no app de lista de tarefas, utilizando:
- **Room Database (SQLite)** para armazenar tarefas
- **SharedPreferences** para configurações (ex: tema escuro)

---

## 📁 Estrutura
```
data/
 ├── model/
 │   └── Task.kt
 ├── dao/
 │   └── TaskDao.kt
 └── database/
     └── AppDatabase.kt
```

---

## 🗃️ Dependências (build.gradle)
```groovy
plugins {
    id 'com.android.application'
    id 'org.jetbrains.kotlin.android'
    id 'com.google.devtools.ksp' version '1.9.0-1.0.13'
}

dependencies {
    def room_version = "2.6.1"
    implementation "androidx.room:room-runtime:$room_version"
    ksp "androidx.room:room-compiler:$room_version"
    implementation "androidx.room:room-ktx:$room_version"
}
```

---

## ⚙️ Passos para usar
1️⃣ Copie a pasta `data/` para dentro do projeto base clonado de:
   ```
   https://github.com/thyerrimezzari/BaseToDoListCompose
   ```

2️⃣ Sincronize o Gradle no Android Studio  
3️⃣ Rode o app normalmente (Room criará o banco automaticamente)

---

## 🧩 Uso básico
```kotlin
val db = AppDatabase.getDatabase(context)
val dao = db.taskDao()

lifecycleScope.launch {
    dao.insert(Task(title = "Nova tarefa"))
    val tasks = dao.getAll()
    tasks.forEach { Log.d("TASK", it.title) }
}
```

---

## 📘 Créditos
Baseado nas aulas do Prof. Thyerri Mezzari (UNISATC)
Implementação: [Vitória do Amaral Viana]
