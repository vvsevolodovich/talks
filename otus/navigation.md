# Навигация и AsyncStorage

---

# Видно? Слышно?

---

# Владимир Иванов

* Solution Architect at EPAM Systems
* Ex React-Native Mentoring Program Global Curator

![right](me.jpg)

---

# План

* Login Screen
* React Navigation
* Использование AsyncStorage
* Используем токен в API

---

# Login Screen

---

```xml

      <View style={{flexGrow: 1, justifyContent: 'center', padding: 20 }}>
        <View>
          <Input
            value={login}
            onChangeText={login}
          />
          <Input
            value={password}
            onChangeText={password}
          />
          {this.props.loading && <ActivityIndicator />}
          <Button
            title="LOGIN"
            onPress={() => {
              doLogin();
            }}
          />
        </View>
      </View>
```


---

![fit](login.png)

---

# Navigation

---

![center fit](screen.png)

---

![center](react-navigation.png)

---

# Navigators

* Stack Navigator
* Tab Navigator
* Switch Navigator

---

```js

import { createAppContainer } from 'react-navigation';
import { createStackNavigator } from 'react-navigation-stack';

```

---

![](add-stack.png)

---

```js

import LoginScreen from './LoginScreen';

const AppNavigator = createStackNavigator({
  Login: {
    screen: LoginScreen,
  },
});

export default createAppContainer(AppNavigator);

```

---

```js

import Navigation from './src/navigation';

const AppContainer = () => (
  <Provider store={store}>
    <ThemeProvider theme={theme}>
      <Navigation />
    </ThemeProvider>
  </Provider>
);
export default AppContainer;

```

---

```js 

const AppNavigator = createStackNavigator({
  Login: {
    screen: LoginScreen,
  },
  Screen: {
    screen: MainScreen,
  },
});

```
---

```js
          <Button
            title="LOGIN"
            onPress={() => {
              this.props.navigation.navigate('MainScreen');
            }}
          />
```

---

# Is it what it should work like?

---

# Login screen is on the back stack

---

## SwitchNavigator

---
```js

import {createAppContainer, createSwitchNavigator} from 'react-navigation';


```

---

```js

const AuthenticatedStack = createStackNavigator({
  RootScreen: {
    screen: MainScreen,
  },
});

const AppNavigator = createSwitchNavigator({
  Login: {
    screen: LoginScreen,
  },
  Main: {
    screen: AuthenticatedStack,
  },
});

```

---

```js
const AuthenticatedStack = createStackNavigator({
  RootScreen: {
    screen: MainScreen,
  },
  NewPost: {
    screen: NewPostScreen,
  },
});
```
---

# Features

* Passing params
* Customizing header
* Navigation lifecycle
* Modals
* etc.

---

# Customizing headers

```xml

  static navigationOptions = {
    headerTitle: () => <Text>New Post</Text>,
    headerRight: () => (
      <Button
        onPress={() => alert('This is a button!')}
        title="Info"
        color="#fff"
      />
    ),
  };

```

---

![fit](header.png)

---

# Async Storage

---

![fit](add-async.png)

---

* Always abstract Storage

---

```js

import AsyncStorage from '@react-native-community/async-storage';

const AUTH_TOKEN_KEY = 'auth_token';

export const saveToken = async token => {
  try {
    await AsyncStorage.setItem(AUTH_TOKEN_KEY, token);
  } catch (e) {
    console.log(e);
  }
};

export const loadToken = async () => {
  try {
    return await AsyncStorage.getItem(AUTH_TOKEN_KEY);
  } catch (e) {
    console.log(e);
  }
};


``` 

---

```xml
          <Button
            title="LOGIN"
            onPress={async () => {
              await saveToken('mytesttoken')
              this.props.navigation.navigate('Main');
            }}
          />
```

---

# What about auth screen?

---

# You can't have dynamic initial route name

---

```js

class AuthLoadingScreen extends React.Component {
  componentDidMount() {
    setTimeout(() => {
      this._bootstrapAsync();
    }, 1000);
  }

  // Fetch the token from storage then navigate to our appropriate place
  _bootstrapAsync = async () => {
    const userToken = await loadToken();
    console.log(userToken);
    this.props.navigation.navigate(userToken ? 'Main' : 'Login');
  };

  render() {
    return (
      <View style={{ flex: 1, alignItems: 'center' }}>
        <ActivityIndicator />
      </View>
    );
  }
}

```
---

```js, [.highlight: 1-6]

class AuthLoadingScreen extends React.Component {
  componentDidMount() {
    setTimeout(() => {
      this._bootstrapAsync();
    }, 1000);
  }

  // Fetch the token from storage then navigate to our appropriate place
  _bootstrapAsync = async () => {
    const userToken = await loadToken();
    console.log(userToken);
    this.props.navigation.navigate(userToken ? 'Main' : 'Login');
  };

  render() {
    return (
      <View style={{ flex: 1, alignItems: 'center' }}>
        <ActivityIndicator />
      </View>
    );
  }
}

```
---

```js, [.highlight: 7-13]

class AuthLoadingScreen extends React.Component {
  componentDidMount() {
    setTimeout(() => {
      this._bootstrapAsync();
    }, 1000);
  }

  // Fetch the token from storage then navigate to our appropriate place
  _bootstrapAsync = async () => {
    const userToken = await loadToken();
    console.log(userToken);
    this.props.navigation.navigate(userToken ? 'Main' : 'Login');
  };

  render() {
    return (
      <View style={{ flex: 1, alignItems: 'center' }}>
        <ActivityIndicator />
      </View>
    );
  }
}

```

---

```js, [.highlight: 15-20]

class AuthLoadingScreen extends React.Component {
  componentDidMount() {
    setTimeout(() => {
      this._bootstrapAsync();
    }, 1000);
  }

  // Fetch the token from storage then navigate to our appropriate place
  _bootstrapAsync = async () => {
    const userToken = await loadToken();
    console.log(userToken);
    this.props.navigation.navigate(userToken ? 'Main' : 'Login');
  };

  render() {
    return (
      <View style={{ flex: 1, alignItems: 'center' }}>
        <ActivityIndicator />
      </View>
    );
  }
}

```
---

# Axios 

```js

axios.post('/user', {
    firstName: 'Fred',
    lastName: 'Flintstone'
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });

```
---

# Configure an instance

```js

const instance = axios.create({
  baseURL: 'https://some-domain.com/api/',
  timeout: 1000,
  headers: {'X-Custom-Header': 'foobar'}
});

```

---

# In a request

```js
axios({
  method: 'post',
  url: '/user/12345',
  data: {
    firstName: 'Fred',
    lastName: 'Flintstone'
  },
  headers: {
        'Authorization': 'Basic Y2xpZW50OnNlY3JldA==',
        'Content-Type': 'application/x-www-form-urlencoded'
    },
});

```
---

# Or global

```js

axios.defaults.headers.common['Authorization'] = AUTH_TOKEN;

```
---

# That's all!

---

# Resume

* Login Screen
* React Navigation
* Использование AsyncStorage
* Используем токен в API

---

# Links

* https://reactnavigation.org/en/
* https://github.com/react-native-community/async-storage/blob/LEGACY/docs/API.md

---

# QA
 
