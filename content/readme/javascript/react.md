---
title: "React"
date: 2020-12-1T17:13:36+02:00
draft: false
---

# React Native Components

## Swipeable 
Swiping gesture to swipe in content like buttons.

Useful when you want to mimic the interaction on iOS and Android.

**Example:**
```
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

### Documentation
https://software-mansion.github.io/react-native-gesture-handler/docs/component-swipeable.html





