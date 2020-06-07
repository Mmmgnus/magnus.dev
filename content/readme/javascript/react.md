---
title: "React"
date: 2020-12-1T17:13:36+02:00
draft: false
---
## State

### Change state when props has changed
It is possible to update the local state when a prop is changed. 

```javascript
componentWillRecieveProps (nextProps) {
	if (nextProps.user.data.isFollowing !== this.props.user.data.isFollowing) {
		this.setState({ loading: false})
	}
}
```

This example code comes from a scenario where a component has a button to start following the user. When pressed, the button displays a loading spinner. When the button is pressed the loading state change to true:

```javascript
	onPressFollowHandler () {
    this.setState({ loading: true })
    this.props.onPressFollow()
  }
```

Then the component waits for the prop containing the following information to update with the `componentWillRecieveProps` function.

## React Native Components

### Swipeable 
Swiping gesture to swipe in content like buttons.

Useful when you want to mimic the interaction on iOS and Android to remove list items.

**Example:**
```javascript
<Swipeable
	ref={this.updateRef}
	friction={2}
	rightThreshold={40}
	overshootRight={false}
	renderRightActions={this.renderRightActions}
>
	{children}
</Swipeable>
```


#### Documentation
https://software-mansion.github.io/react-native-gesture-handler/docs/component-swipeable.html

### AsyncStorage
https://medium.com/building-with-react-native/what-is-asyncstorage-in-react-native-and-how-you-to-use-it-with-app-state-manager-1x09-b8c636ce5f6e

### React Native ReAnimated
#### Animate opacity
- https://stackoverflow.com/questions/60574883/how-to-do-a-simple-opacity-animation-using-functional-components-and-react-nativ

## Issues & problems
Collect all issues and problems that I had with React and how I solved them.

### Config ESlint in create-react-app
I had a problem with configuring ESLint in a newly created react app. I used create-react-app to help me create the app.

My goal was to configure ESlint to use the "standard" code style. And by adding ESlint to the project manually, I got errors. Create-react-app already have ESlint and by adding it manually I introducing a lot of issues.

My initial problem was that I did not know how run aslant in the project from the terminal. I found plenty of issues regarding this in the [GitHub repo](https://github.com/facebook/create-react-app/issues/1217) and it seems that their was as fix this in the making. But some people recommended to run it from en node_modules folder:

```
$ ./node_modules/.bin/eslint src
```

So I added it as a script in my package.json file:
```
"lint": "./node_modules/.bin/eslint src",
```

Next step was to change the listing rules to follow "standard" code style.

First I tried to extend the config:
```
"eslintConfig": {
	"extends": [
	  "react-app",
	  "standard"
	]
},
```

ESlint did thow some helpful errors in my face:
```
[Info  - 14:57:47] Failed to load config "standard" to extend from. Referenced from: /Users/magnus/code/work/creator-tool/package.json
[Info  - 14:58:37] Failed to load plugin 'node' declared in 'package.json » eslint-config-standard': Cannot find module 'eslint-plugin-node' Require stack: - /Users/magnus/code/work/creator-tool/__placeholder__.js
```

I fixed this by adding the missing dependencies.
```
"devDependencies": {
	"eslint-config-standard": "^14.1.1",
	"eslint-plugin-import": "^2.20.2",
	"eslint-plugin-node": "^11.1.0",
	"eslint-plugin-promise": "^4.2.1",
	"eslint-plugin-react": "^7.20.0",
	"eslint-plugin-standard": "^4.0.1"
},
```
