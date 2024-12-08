When building Android apps, things like screen rotations can cause your activity to restart. This means any data not saved properly might reset to default values. Here’s how to keep your data intact using different methods:
#### **1. Serializable**

- **What It Is:** A simple way to turn objects into a format that can be easily saved or passed around.
- **How to Use:** Just have your class implement the `Serializable` interface.
- **Pros:** Easy to implement.
- **Cons:** Slower and not the best for Android-specific tasks.
#### **2. Parcelable**

- **What It Is:** A faster, Android-optimized way to serialize objects.
- **How to Use:** Implement the `Parcelable` interface in your class. Kotlin’s `@Parcelize` makes this easier.
- **Pros:** Better performance on Android.
- **Cons:** More setup compared to Serializable.
#### **3. `rememberSaveable` in Jetpack Compose**

- **What It Is:** A Compose function that saves state across activity recreations, like screen rotations.
- **How to Use:**
    `var text by rememberSaveable { mutableStateOf("") }`
- **Pros:** Seamlessly integrates with Compose; great for simple data.
- **Cons:** Best for basic types (e.g., Int, String). Custom objects need Parcelable or Serializable.
#### **4. Using Primitives and Default Values**

- **What It Is:** Storing simple data types like integers or strings directly.
- **How to Use:** Keep your data in basic variables that naturally survive state changes.
- **Pros:** Simple and straightforward.
- **Cons:** Not suitable for complex data without extra work.
### **Quick Tips**

- **Choose Wisely:** Use `Parcelable` for better performance on Android. Use `Serializable` if you want simplicity.
- **Leverage Compose:** `rememberSaveable` is your friend for keeping UI state smooth.
- **Keep It Simple:** Use basic data types when you can to avoid complications.
- **Handle Custom Data Carefully:** Make sure any custom objects are Parcelable or Serializable if you need to save them.

By using these methods, you can ensure your app retains important data even when the activity restarts, providing a smoother experience for your users.