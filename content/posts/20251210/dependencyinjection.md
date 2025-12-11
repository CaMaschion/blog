---
title: "Understanding Dependency Injection in Android"
date: 2025-12-10T09:00:00+01:00
draft: true
tags: ["Android", "Kotlin", "Dependency Injection", "Hilt", "Dagger", "Clean Architecture"]
categories: ["Android Development"]
---

# **Dependency Injection in Android (no long boring lecture, I promise 😌)**

You know when you’re happily coding, just trying to set up a simple ViewModel, and suddenly you realize you need to wire up a Repository, a Service, Retrofit, a Database, authentication, caching…
And your brain goes: “Ok, but… the Activity is definitely NOT where this belongs. So where do I even put all of this? How am I supposed to fit ALL these dependencies without turning this into a Frankenstein?”

At this point, you're not dealing with a ViewModel anymore — you're dealing with too many things knowing too many things.
And that’s exactly where **Dependency Injection** comes to the rescue.

Instead of having your classes create and manage everything themselves, DI lets them simply receive what they need — clean, organized, and testable.

And to explain this without sounding like a software architecture textbook, let’s use the most universal metaphor ever: **coffee**.

---

## ☕ **The chaotic coffee shop vs. the smart one**

### **Without DI — The chaotic, old-school coffee shop**

Imagine a barista who, before making your espresso, needs to:

- Build the coffee machine from scratch  
- Plant, harvest, and grind the beans  
- Adjust water pressure manually  
- And *then* finally make your coffee

That’s an Android class creating all of its dependencies manually.  
Does it work? Sure.  
Is it fun? Absolutely not. Is it maintainable? Even less. Testing? Forget it.

---

### **With DI — The modern and happy coffee shop**

Now imagine the barista simply saying:

> “Can someone get me a CoffeeMachine and some Beans?” (`@Inject`)

And the manager — **Hilt** — delivers everything ready to use.  
If tomorrow the shop switches machines or beans, the barista doesn't even notice. They just use whatever is handed to them.

That’s the whole idea behind **Dependency Injection**:  
**the one who *uses* the objects is not the one who decides *how* they are created.**

---

## **DI according to the official documentation**

The Android docs put it like this:

> *“Classes often require references to other classes. These required classes are called dependencies.”*

When a class creates everything internally, we get **tight coupling**.  
Want to switch an Engine for a TestEngine? Want to mock something? Want to refactor?  
Well… good luck.

With DI, the responsibility flips:  
**dependencies are provided from the outside**, not created inside.

---

## **Hilt: the official manager of the Android coffee shop**

The officially recommended DI solution for Android is **Hilt**, built on top of Dagger but SO much easier to use daily.

It gives you:

- Less boilerplate  
- Ready-to-use scopes (`SingletonComponent`, `ActivityComponent`, etc.)  
- Native integration with Activity, Fragment, Service, Compose, ViewModel  
- Much easier testing  
- Compile-time safety  

Basically, DI without headaches.

---

## **The essential annotations (the ones you use EVERY SINGLE DAY)**

### **`@HiltAndroidApp`**

Goes on your `Application` class.  
Enables Hilt and generates all base components.

---

### **`@AndroidEntryPoint`**

Marks Activities, Fragments, Services, or Composables that should receive dependencies.

Example:

```kotlin
@AndroidEntryPoint
class MainActivity : AppCompatActivity() { ... }
```

---

### **`@Inject`**

The cleanest way to receive dependencies.
The docs strongly recommend using **constructor injection** whenever possible.

Example:

```kotlin
class MyRepository @Inject constructor(
    private val api: ApiService
)
```

---

### **`@Module` + `@InstallIn`**

When you *can't* use `@Inject` (interfaces, external libraries, classes you don't control), you create modules.

A Hilt module is a class annotated with `@Module` that informs Hilt how to provide or bind types you can’t constructor-inject (like interfaces or external library classes). 

All Hilt modules must also have an `@InstallIn` annotation, which specifies the Hilt component (or container) where those bindings should be available (e.g., SingletonComponent for app-wide or ActivityComponent for activity-scoped). 

The component you choose determines the lifecycle and visibility of the provided dependencies (bindings become available in that component and its children).


### **`@Provides` / `@Binds`**

Tell Hilt how to create a dependency.

Example:

```kotlin
@Module
@InstallIn(SingletonComponent::class)
object NetworkModule {

    @Provides
    fun provideRetrofit(): Retrofit =
        Retrofit.Builder()
            .baseUrl("https://api.example.com")
            .build()
}
```

---

## **To wrap it up**

* DI is about *not* being the barista who builds the coffee machine every time.
* Hilt is the officially recommended DI approach for Android.
* Constructor `@Inject` is your best friend.
* Modules exist for things you can’t control.
* Testing becomes *way* easier.

---

## **Official Sources**

**Dependency Injection — Android Developers**
[https://developer.android.com/training/dependency-injection](https://developer.android.com/training/dependency-injection)

**Hilt and Dagger — Android Developers**
[https://developer.android.com/training/dependency-injection/hilt-android](https://developer.android.com/training/dependency-injection/hilt-android)

**Hilt Guide & Annotations — Android Developers**
[https://developer.android.com/training/dependency-injection/hilt-android#annotations](https://developer.android.com/training/dependency-injection/hilt-android#annotations)

**Hilt Modules & Components — Android Developers**
[https://developer.android.com/training/dependency-injection/hilt-android#modules-components](https://developer.android.com/training/dependency-injection/hilt-android#modules-components)

**Hilt: Testing with Hilt — Android Developers**
[https://developer.android.com/training/dependency-injection/hilt-testing](https://developer.android.com/training/dependency-injection/hilt-testing)

**Hilt Codelab — Android Developers**
[https://developer.android.com/codelabs/android-hilt](https://developer.android.com/codelabs/android-hilt)

**Dagger Hilt (Official Documentation) — dagger.dev**
[https://dagger.dev/hilt](https://dagger.dev/hilt)

