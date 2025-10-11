
<a href="https://github.com/drshahizan/mobile_apps/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/mobile_apps" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/mobile_apps/network/members"><img src="https://img.shields.io/github/forks/drshahizan/mobile_apps" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/mobile_apps/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/mobile_apps" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/mobile_apps/issues"><img src="https://img.shields.io/github/issues/drshahizan/mobile_apps" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/mobile_apps/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/mobile_apps?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2Fmobile_apps&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Your First Flutter App Tutorial

This tutorial guides you through building your first Flutter app: a name generator that creates random word pairs (e.g., "newstay" or "lightstream"). Users can generate new names, favorite them, and view a list of favorites on a separate page. The app is responsive, uses Material Design, and incorporates state management with the Provider package. By the end, you'll have a functional, navigable app that runs on mobile, web, or desktop.

This is based on the official Flutter codelab. It assumes you've installed Flutter and set up your development environment (e.g., VS Code with the Flutter extension). If not, refer back to the installation steps from our previous conversation.

The app starts simple and builds up, teaching key concepts like widgets, state management, layouts, and navigation. Estimated time: 1-1.5 hours.

## Prerequisites
- Flutter SDK installed.
- VS Code (recommended) with the Flutter and Dart extensions.
- A target platform (e.g., Android emulator, iOS simulator, web browser, or desktop).
- Basic Dart knowledge (Flutter uses Dart).
- Git for dependencies (already set up during installation).

**Tips**: 
- Use hot reload (save file or press 'r' in the terminal) to see changes instantly without restarting.
- Web doesn't support stateful hot reload fully.
- Run `flutter doctor` to verify your setup.

## Step 1: Create a New Flutter Project
1. Open VS Code.
2. Open the Command Palette (Ctrl+Shift+P on Windows/Linux, Cmd+Shift+P on macOS).
3. Type and select "Flutter: New Project".
4. Choose "Application" as the project type.
5. Select a folder for the project (e.g., `~/development` or `C:\src`).
6. Name the project (e.g., `namer_app`).
7. VS Code will create the project and open it.

This generates a basic structure with files like `pubspec.yaml`, `analysis_options.yaml`, and `lib/main.dart`.

## Step 2: Set Up the Scaffold Files
Overwrite the following files with the provided code to start with a basic scaffold. This includes dependencies for random words (`english_words`) and state management (`provider`).

### `pubspec.yaml` (App metadata and dependencies)
```yaml
name: namer_app
description: "A new Flutter project."
publish_to: "none"
version: 0.1.0
environment:
  sdk: ^3.9.0
dependencies:
  flutter:
    sdk: flutter
  english_words: ^4.0.0
  provider: ^6.1.5
dev_dependencies:
  flutter_test:
    sdk: flutter
  flutter_lints: ^6.0.0
flutter:
  uses-material-design: true
```

Run `flutter pub get` in the terminal to install dependencies.

### `analysis_options.yaml` (Code linting rules, relaxed for beginners)
```yaml
include: package:flutter_lints/flutter.yaml
linter:
  rules:
    avoid_print: false
    prefer_const_constructors_in_immutables: false
    prefer_const_constructors: false
    prefer_const_literals_to_create_immutables: false
    prefer_final_fields: false
    unnecessary_breaks: true
    use_key_in_widget_constructors: false
```

### `lib/main.dart` (Entry point and basic UI)
```dart
import 'package:english_words/english_words.dart';
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return ChangeNotifierProvider(
      create: (context) => MyAppState(),
      child: MaterialApp(
        title: 'Namer App',
        theme: ThemeData(
          colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepOrange),
        ),
        home: MyHomePage(),
      ),
    );
  }
}

class MyAppState extends ChangeNotifier {
  var current = WordPair.random();
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    var appState = context.watch<MyAppState>();
    return Scaffold(
      body: Column(
        children: [
          Text('A random idea:'),
          Text(appState.current.asLowerCase)
        ],
      ),
    );
  }
}
```

**Explanation**:
- `main()` launches the app.
- `MyApp` sets up the app theme, state provider, and home page.
- `MyAppState` holds app state (e.g., current word pair) and notifies widgets of changes.
- `MyHomePage` displays the UI using a `Scaffold` (basic app structure) and `Column` (vertical layout).
- Widgets are immutable; `build()` rebuilds them as needed.

Save and run the app (press the play button in VS Code or run `flutter run` in terminal). Select a device/emulator. You should see "A random idea:" followed by a random word pair.

## Step 3: Add a Button and Interactivity
Update `MyHomePage`'s `build` method to add a button:

```dart
@override
Widget build(BuildContext context) {
  var appState = context.watch<MyAppState>();
  return Scaffold(
    body: Column(
      children: [
        Text('A random AWESOME idea:'),
        Text(appState.current.asLowerCase),
        ElevatedButton(
          onPressed: () {
            print('button pressed!');
          },
          child: Text('Next'),
        ),
      ],
    ),
  );
}
```

Hot reload (save file). A "Next" button appears. Pressing it logs to the console.

Now, add real behavior. In `MyAppState`, add:

```dart
void getNext() {
  current = WordPair.random();
  notifyListeners();
}
```

Update the button's `onPressed`:

```dart
onPressed: () {
  appState.getNext();
},
```

Hot reload and test: Pressing "Next" generates a new word pair.

**Tips**:
- `notifyListeners()` triggers UI rebuilds for watching widgets.
- Use the Debug Console in VS Code to see logs.

## Step 4: Improve the UI (Styling and Layout)
Extract the word display into a reusable widget for better organization.

In `MyHomePage`, add `var pair = appState.current;` and change to `Text(pair.asLowerCase)`.

Right-click the `Text` widget and select "Extract Widget" (or Ctrl+.). Name it `BigCard`.

Update `BigCard`:

```dart
class BigCard extends StatelessWidget {
  const BigCard({super.key, required this.pair});
  final WordPair pair;

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    final style = theme.textTheme.displayMedium!.copyWith(
      color: theme.colorScheme.onPrimary,
    );
    return Card(
      color: theme.colorScheme.primary,
      elevation: 4, // Optional: Adds shadow
      child: Padding(
        padding: const EdgeInsets.all(20),
        child: Text(
          pair.asLowerCase,
          style: style,
          semanticsLabel: "${pair.first} ${pair.second}", // For accessibility
        ),
      ),
    );
  }
}
```

In `MyHomePage`, replace with `BigCard(pair: pair)`.

Center the content: Wrap `Column` in `Center`, set `mainAxisAlignment: MainAxisAlignment.center`.

Add spacing: `SizedBox(height: 10)` between `BigCard` and button.

**Explanation**:
- `Theme.of(context)` accesses app theme for consistent styling.
- `Card` and `Padding` make it look like a card.
- Semantics improve accessibility (e.g., screen readers say words separately).
- Experiment with `seedColor` in `ThemeData` for different colors.

Hot reload to see the prettier UI.

## Step 5: Add Favorites Functionality
In `MyAppState`, add a favorites list:

```dart
var favorites = <WordPair>[];

void toggleFavorite() {
  if (favorites.contains(current)) {
    favorites.remove(current);
  } else {
    favorites.add(current);
  }
  notifyListeners();
}
```

In `MyHomePage`, add logic for the icon:

```dart
IconData icon;
if (appState.favorites.contains(pair)) {
  icon = Icons.favorite;
} else {
  icon = Icons.favorite_border;
}
```

Wrap buttons in a `Row` (horizontal layout) with `mainAxisSize: MainAxisSize.min`:

```dart
Row(
  mainAxisSize: MainAxisSize.min,
  children: [
    ElevatedButton.icon(
      onPressed: () { appState.toggleFavorite(); },
      icon: Icon(icon),
      label: Text('Like'),
    ),
    SizedBox(width: 10),
    ElevatedButton(
      onPressed: () { appState.getNext(); },
      child: Text('Next'),
    ),
  ],
),
```

Hot reload: Now you can "Like" names, and the icon changes.

## Step 6: Add Navigation (Multiple Pages)
To add a favorites page, make the app navigable. Extract the generator UI to `GeneratorPage` (as in the code from Step 2 scaffold, but updated with current changes).

Convert `MyHomePage` to a `StatefulWidget` (for tracking selected page):

Right-click `MyHomePage` class name > Refactor > Convert to StatefulWidget.

In `_MyHomePageState`, add `var selectedIndex = 0;`.

Update `build`:

```dart
@override
Widget build(BuildContext context) {
  Widget page;
  switch (selectedIndex) {
    case 0:
      page = GeneratorPage();
      break;
    case 1:
      page = FavoritesPage(); // Create this next
      break;
    default:
      throw UnimplementedError('no widget for $selectedIndex');
  }

  return LayoutBuilder(
    builder: (context, constraints) {
      return Scaffold(
        body: Row(
          children: [
            SafeArea(
              child: NavigationRail(
                extended: constraints.maxWidth >= 600, // Responsive: Extend on wide screens
                destinations: [
                  NavigationRailDestination(
                    icon: Icon(Icons.home),
                    label: Text('Home'),
                  ),
                  NavigationRailDestination(
                    icon: Icon(Icons.favorite),
                    label: Text('Favorites'),
                  ),
                ],
                selectedIndex: selectedIndex,
                onDestinationSelected: (value) {
                  setState(() {
                    selectedIndex = value;
                  });
                },
              ),
            ),
            Expanded(
              child: Container(
                color: Theme.of(context).colorScheme.primaryContainer,
                child: page,
              ),
            ),
          ],
        ),
      );
    },
  );
}
```

Create `FavoritesPage`:

```dart
class FavoritesPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    var appState = context.watch<MyAppState>();
    if (appState.favorites.isEmpty) {
      return Center(
        child: Text('No favorites yet.'),
      );
    }
    return ListView(
      children: [
        Padding(
          padding: const EdgeInsets.all(20),
          child: Text('You have ${appState.favorites.length} favorites:'),
        ),
        for (var pair in appState.favorites)
          ListTile(
            leading: Icon(Icons.favorite),
            title: Text(pair.asLowerCase),
          ),
      ],
    );
  }
}
```

**Explanation**:
- `StatefulWidget` allows mutable state (e.g., `selectedIndex`).
- `NavigationRail` provides sidebar navigation, responsive with `LayoutBuilder`.
- `switch` selects the page; `Expanded` fills the space.
- `FavoritesPage` uses `ListView` for scrollable favorites list.
- `setState` triggers rebuild on navigation.

Hot reload: Now navigate between Home (generator) and Favorites. On wide screens (e.g., desktop), the rail extends with labels.

## Step 7: Make It Responsive and Polish
The app is already responsive via `LayoutBuilder` (rail extends on screens >=600px wide).

Optional polish:
- In `toggleFavorite`, pass an optional next pair for smoother transitions.
- Add removal from favorites in `FavoritesPage`.
- Customize theme further (e.g., dark mode support).
- Test on different platforms.

## Final Tips
- Run `flutter test` for unit tests (add them as you go).
- Debug with VS Code's debugger (set breakpoints).
- For production: Build with `flutter build` (e.g., `flutter build apk` for Android).
- Explore more: Add animations, persistence (e.g., save favorites), or deploy to app stores.
- Common issues: If hot reload fails, restart the app. Check console for errors.

Congratulations! You've built your first Flutter app. Experiment and build on this foundation. For more codelabs, check the official Flutter docs.

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/mobile_apps/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)


