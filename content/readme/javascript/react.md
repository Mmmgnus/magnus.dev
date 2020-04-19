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





