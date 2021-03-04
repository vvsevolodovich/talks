slidenumbers: true
autoscale: true
build-lists: true
footer: @vvsevolodovich

#[fit] Jetpack Compose, Figma and Feedback Loop.
## and more!

---

# [fit] Vladimir Ivanov

* Solution Architect @ Tinkoff
* Experience with native Android, React-Native, Flutter, etc.

![right](newme.jpg)

---

# Joe

## Delivery Manager

![right](Joe.jpeg)

---


![center fit](https://i.pinimg.com/originals/0a/73/9b/0a739b78a09ceed490b03c17ece6a10f.png)

---

### Value stream

# [fit] sequence of steps taken by the organization 
# [fit] to __continuously__ bring __value__ to the users[^1]

[^1]: https://www.cloudbees.com/blog/value-stream-management-software-delivery-visibility-and-insight

---

# Jane

## [fit] Android developer

![fit right](jane11.png)

---

Screen design&requirements

![fit right](sleeptracker.png)

---

Screen design&requirements
:arrow_down:
Code

![fit right](sleeptracker.png)

---

Screen design&requirements
:arrow_down:
Code
:arrow_down:
Unit tests

![fit right](sleeptracker.png)

---

Screen design&requirements
:arrow_down:
Code
:arrow_down:
Unit tests
:arrow_down:
Merge request

![fit right](sleeptracker.png)

---

Screen design&requirements
:arrow_down:
Code
:arrow_down:
Unit tests
:arrow_down:
Merge request
:arrow_down:
Functional & Design Test

![fit right](sleeptracker.png)

---

![fit center](feedback.png)

---

![fit](https://i.kym-cdn.com/entries/icons/facebook/000/000/091/TrollFace.jpg)

---

# Issues

* Manual design verification :thumbsdown:
* Context Switch :thumbsdown:

---

![fit center](https://alchetron.com/cdn/gerald-weinberg-86dc73f4-db9b-49ec-926f-24340fb88ea-resize-750.jpg)

---

> Each extra task or ‘context’ you switch between eats up 20–80% of your overall productivity
-- Gerald Weinberg


---

Challenge!

Guess how many times I switched between tasks during preparing this talk

---

# Ideas 

* Introduce Storybook

![fit right](jane13.png)

---

![center](https://raw.githubusercontent.com/storybookjs/storybook/master/media/storybook-intro.gif)

---

#[fit] https://github.com/airbnb/Showkase

---

![center fit](https://github.com/airbnb/Showkase/raw/master/assets/showkase_demo.gif)

---

```kotlin
@Preview(
	name = "Custom name", 
	group = "Custom group name"
)
@Composable
fun MyComponent() { ... }
```

---

```kotlin
@ShowkaseComposable(
	name = "Name of component", 
	group = "Group Name"
)
@Composable
fun MyComponent() { ... }
```

---

```dart
List<Story> stories = [
  HomeStory(),
  SignInScreenStory()
];

void main() {
  runApp(StoryboardApp(stories));
}
```

---

```dart
import 'package:mypackage/contacts.dart';
import 'package:storyboard/storyboard.dart';

class ContactsListStory extends Story {

  @override
  List<Widget> get storyContent {
    return [ContactsList()];
  }
}
```

---

# Benefits 

Fast Debug of a component 
Easy way to share for design review
:arrow_down:
Reduced Feedback loop :thumbsup:

---

# Pixel perfect is still hardly achievable :thumbsdown:

![fit right](jane12.png)

---

![fit](https://prosperityconnection.org/wp-content/uploads/2020/04/What-If.jpg)

---

## Jetpack Compose Figma Preview

---

```kotlin

@Preview
@Composable
fun figmaPreviewPreview() {
    FigmaPreview(
	fileId = "yourfileid", 
	id = "1:405", 
	token = "blablablayourtoken"
    )
}

```

---

# Flutter Figma Preview

---

[.code-highlight: 0-100]
[.code-highlight: 5-10]
[.code-highlight: 6]
[.code-highlight: 7]
[.code-highlight: 10]

```dart

      Title(
        title: "Full Screen Example - 2911:367",
        color: Colors.black,
        child: SafeArea(
          child: FigmaPreview(
              id: '1:295',
              figmaToken: '1234567890xabcde',
              fileId: fileId,
              isFullScreen: true,
              child: IncomingCallScreen(type: CallType.voice),
        ),
      )
```

---

# Flutter Figma Preview

* Component Id
* File Id
* Auth token

---

![fit center](componentscript.png)

---

![fit center](scripter.png)

---

![fit center](figmatoken.png)

---

![fit center](fileid.png)

---

# Search for ids

![fit right](https://github.com/vlivanov/flutter_figma_preview/raw/master/media/search.png)

---

# Take aways

* Feedback loop decreases your velocity
* Use Storyboards to help your designer
* Use JC Figma Preview/Flutter Figma Preview for an immediate feedback

![fit right](jane14.png)

---

# [fit] Vladimir Ivanov

* https://pub.dev/packages/flutter_figma_preview
* https://vvsevolodovich.dev :pencil:
* https://twitter.com/vvsevolodovich :bird:


![right](newme.jpg)
