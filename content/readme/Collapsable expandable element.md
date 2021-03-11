---
title: "Collapsable expandable element"
date: 2021-01-06T18:22:00+02:00
draft: true
---
Something I can't get figured out, it seems, is collapsable/expandable elements, be able to toggle the visibility of an element. For some reason I always go for the expandable approach; "When I click the expandable-class is toggled". I need to get this figured out and move on.

## Required criteria's

* Content need to be accessible without Javascript.
* Flexible, there is not only one way to do collapsable elements. The toggle button and the content should be able to be far apart on a page.
* Accessible with screen readers and keyboard.

## Collapsable vs. expandable

The question comes down to what is the default state. And how much work the javascript should do. Do I want to add a class to the elements that should be hidden or visible?

The expandable way of thinking requires us to have to classes on the elements that can be expanded; one class to hide the element at start and then the class to show the element.

The collapsable way only requires one class because the default state or init state will be visible (no class that hides the element) and the only class used is for hide the element.

## Accessibility

- The button need aria-attributes that should be added with Javascript.
- The button should be created by the script because it does not have any functionality without javascript.

## Instance creation

## Configuration

property | type | default | description
-------- | ---- | ------- | -----------
trigger  | String, Element, Object | '' | String and Element is to use existing element. Object is to create a new button
collapsedClass | String | 'is-hidden | Class that will be used on collapsed elements.

### Trigger object
property | type | default | description
-------- | ---- | ------- | -----------
labelExpanded | String | "Collapse content" |
labelCollapsed | String | "Expand content" |
labelClass | String | ''| Class on the label inside the button.
icon | String | '' | Icon used in the button, recommended to use inline SVG.
class | String | '' | Class on the button.
collapsedClass | String | 'is-active' | Class used on the button when the element is collapsed. 
insertionMethod| String | '' | How we want to add the element to the DOM.
insertionLocation | String, Element | '' | Were we want to add the element in the DOM.

## Scenarios
__The toggler is:__
- a form control for example a radio button.
- a link that is only behaves like a link without javascript.
- a button far away from the collapsable element.


## Code implementation
```
define(function (require) {
	'use strict';

	function collapse (settings, element, index) {
		if (!element && !settings) {
			throw new Error('Missing parameter');
		}

		var id = element.id || settings.idPrefix + index;
		var is_collapsed = element.classList.contains(settings.collapsedClass);
		var trigger = triggerSetup(settings.trigger, is_collapsed, id);

		trigger.addEventListener('click', function () {
			is_collapsed = !is_collapsed;
			toggle(element, trigger, is_collapsed, settings);
		});
	}

	function triggerSetup (trigger_object, is_collapsed, id) {
		var trigger = null;

		switch (typeof trigger_object) {
			case 'Element':
				trigger = trigger_object;
				trigger.setAttribute('aria-controls', id);
				break;

			case 'Object':
				trigger = createTrigger(trigger_object, is_collapsed);
				break;
		}

		return trigger;
	}

	/**
	 * insertionMethod: 'appendTo',
	 * insertionLocation: '#toolbar',
	 * labelTextExpanded: 'Collapse content',
	 * labelTextCollapsed: 'Expand content',
	 * labelClass: 'c-toggle__label',
	 * class: 'c-toggle',
	 * collapsedClass: 'is-active'
	 * @param {Object} trigger_object
	 */
	function createTrigger (trigger_object, is_collapsed) {
		var button = document.createElement('button');
		var label = document.createElement('span');

		button.setAttribute('aria-controls', is_collapsed);

		label.classList.add(trigger_object.class);
		label.innerHTML = (is_collapsed) ? trigger_object.labelTextCollapsed : trigger_object.labelTextExpanded;

		if (trigger_object.icon) {
			button.appendChild(function () {
				var span = document.createElement('span');
				span.classList.add(trigger_object.iconClass);
				span.innerHTML = trigger_object.icon;

				return span;
			}());
		}

		button.appendChild(label);
		var location = document.querySelector(trigger_object.insertionLocation);

		appendElement(button, location, trigger_object.insertionMethod);
	}

	function appendElement (element, location, method) {
		switch (method) {
			case 'append':
				location.appendChild(element);
				break;
		}
	}

	function toggle (element, trigger, is_collapsed, settings) {
		trigger.classList.toggle(settings.trigger.collapsedClass);
		trigger.setAttribute('aria-expanded', is_collapsed);

		element.classList.toggle(settings.collapsedClass);

	}

	function curry (fn) {
		var args = [].slice.call(arguments, 1);

		function curried (fnArgs) {
			if (fnArgs.length >= fn.length) {
				return fn.apply(null, fnArgs);
			}

			return function () {
				return curried(fnArgs.concat([].slice.apply(arguments)));
			};
		}

		return curried(args);
	}

	return curry(collapse);
});
```