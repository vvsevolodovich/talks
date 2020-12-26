slidenumbers: true
autoscale: true
build-lists: true

# React Native: Crossplatform fast dive
![original center](https://saipan.tours/wp-content/uploads/2015/12/skydive1.jpg)

---

# Do you see me? Hear me? Understand me? 

---

#About me

* Vladimir Ivanov - Lead software engineer
* > 8 years in Android development
* ~3 years with React-Native

---

# Today we...

* Find out why React-Native in a first place
* How to start developing
* Take a look on a tiny app

——-

# Why React-Native?

* Allows to use React on Mobile
* So fast and easy development 

——-

# How to dive?

1. Install node
2. Learn React Native
3. [create-react-native-app](https://github.com/react-community/create-react-native-app)
4. Done

——-

Let’s dive

![original center](https://saipan.tours/wp-content/uploads/2015/12/skydive1.jpg)

——-


# What have we got 

```sh

$ ls -l

App.js
App.test.js
README.md
app.json
node_modules
package.json


```

——-


# What have we got 

```sh, [.highlight: 3]

$ ls -l

App.js
App.test.js
README.md
app.json
node_modules
package.json


```

——-

# App.js

```js

import React from 'react';
import { Text, View } from 'react-native';

export default class App extends React.Component {
  render() {
    return (
      <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
        <Text>Hello, world!</Text>
      </View>
    );
  }
}

```


——-

![inline](hello.png)


——-



# App.js

```js, [.highlight: 1]

import React from 'react';
import { Text, View } from 'react-native';

export default class App extends React.Component {
  render() {
    return (
      <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
        <Text>Hello, world!</Text>
      </View>
    );
  }
}


```

——-

# App.js


```js, [.highlight: 2]

import React from 'react';
import { Text, View } from 'react-native';

export default class App extends React.Component {
  render() {
    return (
      <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
        <Text>Hello, world!</Text>
      </View>
    );
  }
}


```

——-


# App.js


```js, [.highlight: 4]

import React from 'react';
import { Text, View } from 'react-native';

export default class App extends React.Component {
  render() {
    return (
      <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
        <Text>Hello, world!</Text>
      </View>
    );
  }
}


```

——-


# App.js

```js, [.highlight: 5,11]

import React from 'react';
import { Text, View } from 'react-native';

export default class App extends React.Component {
  render() {
    return (
      <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
        <Text>Hello, world!</Text>
      </View>
    );
  }
}


```

——-


# App.js


```js, [.highlight: 6-10]

import React from 'react';
import { Text, View } from 'react-native';

export default class App extends React.Component {
  render() {
    return (
      <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
        <Text>Hello, world!</Text>
      </View>
    );
  }
}


```

——-

# App.js

```js

import React from 'react';
import { Text, View } from 'react-native';

export default class App extends React.Component {
  render() {
    return (
      <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
        <Text>Hello, world!</Text>
      </View>
    );
  }
}

```

——-

# App.js

```xml

<Text style={{ color: '#F00' }}>
	Hello, world!
</Text>

```

![right fit](hello-red.png)


——-

# Useful links

- https://facebook.github.io/react-native/docs/getting-started.html
- https://www.udemy.com/the-complete-react-native-and-redux-course/
- https://expo.io
- https://css-tricks.com/snippets/css/a-guide-to-flexbox/

——-

* https://github.com/vlivanov/react-native-fast-dive :computer:


---

# What we learned

* React-Native is a crossplatform framework for Mobile Apps Development
* The start is easy with a couple of console commands
* The UI part of the App with React-Native is a Components Tree

——-

# Questions?
