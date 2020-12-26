slidenumbers: true
autoscale: true
build-lists: true
footer: @vvsevolodovich

#[fit]3F: Flutter, Figma and Feedback Loop

---

# [fit] Vladimir Ivanov

* Solution Architect @ EPAM Systems
* Certified Google Cloud Architect
* Experience with native Android, React-Native, Flutter, etc.

![right](newme.jpg)

---

# Today we learn about

* Value Streams
* Feedback loops
* How to reduce them

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

## [fit] Flutter developer

![fit right](jane11.png)

---

# Typical flow

Screen design&requirements
:arrow_down:
Code
:arrow_down:
Unit tests and flutter analyze
:arrow_down:
Merge request
:arrow_down:
Functional & Design Test

---

![fit center](feedback.png)

---

# Issues

* Manual design verification :thumbsdown:
* Context Switch :thumbsdown:

---

# Ideas 

* Introduce Storybook

![fit right](jane13.png)

---

![center](https://raw.githubusercontent.com/storybookjs/storybook/master/media/storybook-intro.gif)

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

# Take aways

* Feedback loop decreases your velocity
* Use Storyboards to help your designer
* Use Flutter Figma Preview for an immediate feedback

![fit right](jane14.png)

---

# [fit] Vladimir Ivanov

* https://pub.dev/packages/flutter_figma_preview
* https://vvsevolodovich.dev :pencil:
* https://twitter.com/vvsevolodovich :bird:


![right](newme.jpg)
