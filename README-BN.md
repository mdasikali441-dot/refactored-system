# My AI Assistant — Android starter (বাংলা)

এটি একটি প্রাথমিক Android/Kotlin প্রজেক্ট। অ্যাপ চালু করে মাইক্রোফোনের অনুমতি দিলে foreground notification-সহ voice service শুরু করার চেষ্টা করে। এটি SpeechRecognizer-এর মাধ্যমে “হে AI” / “হে এআই” শুনে কিছু নির্দিষ্ট কমান্ড চালায়।

## কমান্ডের উদাহরণ
- “হে AI ইউটিউব খোলো”
- “হে AI ফেসবুক খোলো”
- “হে AI সেটিংস খোলো”
- “হে AI গুগলে বাংলা গান সার্চ করো”
- “হে AI এখন কয়টা বাজে”
- “হে AI বন্ধ করো”

## গুরুত্বপূর্ণ সীমাবদ্ধতা
- এটি production-grade always-on wake-word detector নয়। Android `SpeechRecognizer` API-র ডকুমেন্টেশন অনুযায়ী এটি continuous recognition-এর জন্য তৈরি নয়; অনেক ফোনে recognition থেমে যেতে পারে, ব্যাটারি/ডেটা খরচ হতে পারে, এবং recognition service অডিও রিমোট সার্ভারে পাঠাতে পারে।
- Android 12+ / 14+ এ ব্যাকগ্রাউন্ডে microphone foreground service চালুর সীমাবদ্ধতা আছে। অ্যাপ দৃশ্যমান থাকা অবস্থায় Start চাপুন এবং notification চালু রাখুন।
- নির্ভরযোগ্য “Hey AI” wake word-এর জন্য আলাদা on-device wake-word engine (যেমন Picovoice Porcupine) ও keyword model সেটআপ করতে হবে।
- এই starter সাধারণ কমান্ডের জন্য; এটি নিজে থেকে সব অ্যাপ নিয়ন্ত্রণ, মেসেজ পাঠানো, বা নিরাপত্তা-সীমাবদ্ধ কাজ করতে পারে না।
- “কল” কমান্ড শুধু ডায়ালার খোলে; নিজে থেকে কল করে না।
- AI-র মতো মুক্ত প্রশ্নের উত্তর দিতে একটি নিরাপদ backend/API সংযোগ প্রয়োজন। API key কখনো Android source বা GitHub-এ প্রকাশ করবেন না।

## GitHub দিয়ে APK তৈরি
1. GitHub-এ একটি নতুন repository তৈরি করুন।
2. এই ZIP-এর ফাইলগুলো repository-র root-এ upload করুন; `.github/workflows/build-apk.yml` ফাইলটিও রাখতে হবে।
3. `Actions` tab খুলে `Build Android APK` workflow নির্বাচন করুন; `Run workflow` চাপুন। `main`-এ push করলেও build শুরু হবে।
4. workflow সফল হলে run-এর নিচে `Artifacts` থেকে `MyAIAssistant-debug-apk` নামের artifact download করুন।
5. ZIP artifact extract করে `app-debug.apk` Android ফোনে ইনস্টল করুন। ফোনে “Install unknown apps” অনুমতি চাইতে পারে।

## Android Studio দিয়ে
প্রজেক্টটি Android Studio-তে খুলে Gradle sync করুন এবং Run চাপুন। Gradle wrapper এই starter ZIP-এ অন্তর্ভুক্ত নয়; Android Studio বা GitHub Actions-এর Gradle installation ব্যবহার করুন।
