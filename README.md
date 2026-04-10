# AI Chat

AI Chat is a powerful, fully-featured Android application that provides comprehensive AI-powered chat capabilities using the Pollinations AI API. Built with Kotlin and Material Design 3, it offers a seamless chat experience with multiple AI models, image analysis, and advanced conversation management.

## Features

### Core Functionality
- 💬 **Full Chat Interface** - Natural conversation with AI models using streaming responses
- 🤖 **16+ Free AI Models** - OpenAI, Gemini, Claude, DeepSeek, Perplexity, and more
- 🔄 **Dynamic Model Sync** - Fetch and sync latest available models from Pollinations API
- 🖼️ **Image Analysis** - Attach images to messages for vision-based AI analysis with base64 encoding
- 📝 **Message Management** - Edit, copy, and delete individual messages with confirmation dialogs
- 💾 **Multiple Conversations** - Create, manage, rename, and switch between unlimited conversations
- 📤 **Import/Export** - Backup and restore conversations as JSON files with system prompts
- 🎯 **System Instructions** - Custom system prompts per conversation for personalized AI behavior
- 🗑️ **Multi-Select Delete** - Batch delete conversations with checkbox selection mode
- 🔑 **Optional API Key** - Works without API key via proxy, or use custom Pollinations API key
- 💰 **Balance Checker** - Check API balance directly from settings dialog

### User Interface
- 🌓 **Dark/Light Theme** - Beautiful Material Design 3 UI with persistent theme preference
- 📱 **Material Design 3** - Modern, polished interface with Material components
- 🎨 **Sidebar Navigation** - Smooth drawer with conversation list and edge swipe detection
- 📍 **Scroll Position Memory** - Returns to exact scroll position per conversation
- ⌨️ **Smart Keyboard** - Auto-hides when drawer opens, smart scrolling to last message
- ✨ **Markdown Support** - Rich text formatting in AI responses using Markwon library
- 🔄 **Loading Indicators** - Visual feedback during API calls with loading message bubbles
- 🎯 **Empty State** - Clean empty state UI when no messages exist

### Performance & Quality
- ⚡ **Fast & Smooth** - Optimized with Kotlin Coroutines on Dispatchers.IO
- 🔒 **Crash-Proof** - Comprehensive error handling with try-catch blocks everywhere
- 🚀 **Production-Ready** - Memory leak prevention, proper job cancellation in lifecycle
- 🔄 **Automatic Builds** - CI/CD via GitHub Actions with auto-versioning
- 📦 **Optimized** - Single OkHttp client instance with connection pooling (60s timeouts)
- 🧵 **Thread-Safe** - Proper coroutine lifecycle management with job cancellation
- 💾 **Efficient Storage** - SharedPreferences for conversations and messages with JSON serialization

## Available Models (16 Default + Custom)

The app includes 16 carefully curated default models, with the ability to sync all available models from the Pollinations API:

- **OpenAI GPT-5 Mini** - Fast & Balanced
- **OpenAI GPT-5 Nano** - Ultra Fast & Affordable
- **Qwen3 Coder 30B** - Specialized for Code Generation
- **Mistral Small 3.2 24B** - Efficient & Cost-Effective
- **Google Gemini 2.5 Flash Lite** - Ultra Fast & Cost-Effective
- **DeepSeek V3.2** - Efficient Reasoning & Agentic AI
- **Google Gemini with Search** - Gemini 2.5 Flash Lite with Google Search
- **Anthropic Claude Haiku 4.5** - Fast & Intelligent
- **Perplexity Sonar Fast** - Fast & Affordable with Web Search
- **Perplexity Sonar Reasoning** - Advanced Reasoning with Web Search
- **Moonshot Kimi K2.5** - Flagship Agentic Model with Vision & Multi-Agent
- **Amazon Nova Micro** - Ultra Fast & Ultra Cheap
- **Z.ai GLM-5** - 744B MoE, Long Context Reasoning & Agentic Workflows
- **MiniMax M2.5** - Coding, Agentic & Multi-Language
- **Polly by @Itachi-1824** - Pollinations AI Assistant with GitHub, Code Search & Web Tools (Alpha)
- **Qwen3Guard 8B** - Content Safety & Moderation (OVH)
- **Custom Model** - Enter any model name manually

## Build & CI/CD

### Automatic Builds
The app automatically builds on every push to `main` branch via GitHub Actions:
- Auto-increments version numbers (MAJOR.MINOR.PATCH)
- Creates signed release APKs with keystore
- Publishes releases to GitHub with auto-generated tags

### Manual Build

```bash
./gradlew assembleRelease
```

The signed APK will be in `app/build/outputs/apk/release/`


## Configuration

### API Key (Optional)

The app works **without an API key** using a proxy server. For your own custom API keys:

1. Open Settings (3-dot menu → API Key Settings)
2. Enter your Pollinations AI API key
3. Check balance with "Balance" button
4. Get a key at: https://enter.pollinations.ai

**Direct API URL:** `https://gen.pollinations.ai/v1/chat/completions`

### Model Sync

Sync all available models from Pollinations API:
1. Tap model icon in toolbar
2. Tap "Sync" button
3. Filters models to show only free text-to-text models
4. Synced models persist across app restarts

## How to Use

### Text Chat
1. Type your message in the input field
2. Press send button to chat with AI
3. Responses appear with markdown formatting (bold, italic, code blocks, links)
4. Loading indicator shows while AI is generating response

### Image Analysis
1. Tap the gallery icon to attach an image
2. Select image from gallery (requires READ_MEDIA_IMAGES permission)
3. Image preview appears above input field
4. Type your question about the image
5. Send to get AI analysis with vision-capable models
6. Images are compressed and base64-encoded before sending

### Conversation Management
- **New Chat:** Tap + button in toolbar (only if current chat has messages)
- **Switch Chats:** Open sidebar (swipe from left edge or tap menu icon)
- **Rename:** Long press conversation → Rename
- **Delete Single:** Long press conversation → Delete
- **Multi-Delete:** Long press → Select Multiple → check conversations → delete button
- **Import/Export:** Use Import/Export buttons in sidebar drawer

### Message Actions
- **Copy:** Tap copy icon on any message (user or bot)
- **Edit:** Tap edit icon to modify message text
- **Delete:** Tap delete icon with confirmation dialog

### Settings & Options
- **Model Selection:** Tap model icon in toolbar → select from list or sync new models
- **Dark Mode:** Toggle theme button in toolbar (persists across restarts)
- **System Instructions:** 3-dot menu → System Instructions (per-conversation custom prompts)
- **Delete Conversation:** 3-dot menu → Delete Conversation
- **Clear Chat:** Tap clear icon in toolbar (deletes all messages in current conversation)
- **API Key Settings:** 3-dot menu → API Key Settings (optional, includes balance checker)

## Technical Details

### Architecture
- **Language:** Kotlin
- **UI:** Material Design 3, ViewBinding
- **Async:** Kotlin Coroutines (Dispatchers.IO for network)
- **HTTP:** OkHttp3 with connection pooling (30s connect, 60s read/write timeouts)
- **Storage:** SharedPreferences for conversations and messages
- **Image Loading:** Glide
- **Markdown:** Markwon with Linkify plugin

### Requirements
- Android Studio
- JDK 17+
- Android SDK 34
- Min SDK 24 (Android 7.0+)
- Gradle 8.3.0
- Kotlin 1.9.22

### Dependencies
```gradle
// Core Android
androidx.core:core-ktx:1.12.0
androidx.appcompat:appcompat:1.6.1
com.google.android.material:material:1.11.0
androidx.constraintlayout:constraintlayout:2.1.4
androidx.activity:activity-ktx:1.8.2
androidx.recyclerview:recyclerview:1.3.2

// Networking & Async
com.squareup.okhttp3:okhttp:4.12.0
org.jetbrains.kotlinx:kotlinx-coroutines-android:1.7.3

// UI & Rendering
io.noties.markwon:core:4.6.2
io.noties.markwon:linkify:4.6.2
com.github.bumptech.glide:glide:4.16.0
```

### Permissions
- `INTERNET` - Required for API calls
- `READ_MEDIA_IMAGES` - For image selection (Android 13+)
- `READ_EXTERNAL_STORAGE` - For image selection (Android 12 and below)

### Project Structure

```
app/
├── src/main/
│   ├── java/com/aichat/app/
│   │   ├── MainActivity.kt (1000+ lines) - Main activity with chat UI
│   │   ├── ChatAdapter.kt - RecyclerView adapter for messages
│   │   ├── ConversationAdapter.kt - RecyclerView adapter for conversations
│   │   ├── ConversationManager.kt - Conversation CRUD operations
│   │   ├── ChatMessage.kt - Message data class
│   │   ├── Conversation.kt - Conversation data class
│   │   └── AIChatApp.kt - Application class for theme initialization
│   ├── res/
│   │   ├── layout/
│   │   │   ├── activity_main.xml - Main chat interface
│   │   │   ├── drawer_content.xml - Sidebar navigation
│   │   │   ├── item_message_user.xml - User message layout
│   │   │   ├── item_message_bot.xml - Bot message layout
│   │   │   ├── item_conversation.xml - Conversation list item
│   │   │   ├── dialog_api_key.xml - API key dialog
│   │   │   └── nav_header.xml - Navigation header
│   │   ├── drawable/ - Icons and drawables (light theme)
│   │   ├── drawable-night/ - Icons for dark theme
│   │   ├── values/
│   │   │   ├── strings.xml - String resources
│   │   │   ├── colors.xml - Light theme colors
│   │   │   └── themes.xml - Light theme
│   │   ├── values-night/
│   │   │   ├── colors.xml - Dark theme colors
│   │   │   └── themes.xml - Dark theme
│   │   ├── menu/
│   │   │   └── main_menu.xml - Overflow menu
│   │   ├── mipmap-*/ - App icons (all densities)
│   │   └── xml/
│   │       └── file_paths.xml - File provider paths
│   └── AndroidManifest.xml
├── build.gradle.kts - App-level build configuration
├── proguard-rules.pro - ProGuard rules for release builds
└── release.keystore - Keystore for signing releases
```

### Key Features Implementation

#### Conversation Management
- Uses SharedPreferences with JSON serialization
- Each conversation has unique UUID
- Messages stored separately per conversation ID
- Automatic timestamp sorting

#### Image Handling
- Bitmap compression to 1024x1024 max
- JPEG quality 85% for optimal size/quality
- Base64 encoding for API transmission
- Glide for efficient image loading

#### Scroll Position Memory
- Saves first visible item position and offset per conversation
- Restores exact scroll position when switching conversations
- Smart scrolling to bottom when keyboard opens

#### Theme Persistence
- Stores theme preference in SharedPreferences
- Applies theme in Application class onCreate
- Smooth theme switching without data loss

#### Error Handling
- Try-catch blocks on all critical operations
- Graceful fallbacks for missing data
- User-friendly error messages
- Proper job cancellation to prevent memory leaks

## Performance Optimizations

- Single HTTP client instance (connection pooling)
- Proper coroutine lifecycle management with job cancellation
- Memory leak prevention (job cancellation in onDestroy)
- Efficient RecyclerView with ViewBinding
- Scroll position caching per conversation
- ProGuard rules for release builds
- Image compression before upload
- Lazy initialization of heavy objects (Markwon, OkHttpClient)

## CI/CD Pipeline

### GitHub Actions Workflow
- **Trigger:** Push to `main` branch or tag creation
- **Steps:**
  1. Checkout code with full git history
  2. Setup JDK 17 (Temurin distribution)
  3. Auto-increment version from git tags
  4. Build release APK with Gradle
  5. Rename APK to `AIChat-vX.X.X.apk`
  6. Upload artifact to GitHub Actions
  7. Create GitHub release with APK attachment

## License

This project is open source.
