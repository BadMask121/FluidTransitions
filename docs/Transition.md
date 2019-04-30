# Transition API

The `Transition` element is used to wrap regular React elements that should be transitioned either as part of a shared element transition or as a transition when it appears or disappears.

The element accepts only one child, trying to add multiple children or wrap it in `Fragment` will result in an error.

## Shared Element Transition
A shared element transition happens when two elements in two different screens share the same transition identificator through the `shared` property of the Transition element.

```javascript
<Screen1>
  <Transition shared='common-name'>
    <View>...</View>
  </Transition>
</Screen1>

<Screen2>
  <Transition shared='common-name'>
    <View>...</View>
  </Transition>
</Screen2>
``` 

The `Transition` element must be in a tree of elements where a [`FluidNavigator`](FluidNavigator.md) is the parent view.

## Transition
In addition to taking part in a shared element transition, a `Transition` element can also be used to define how an element should appear and disappear when its screen is navigated to or from.

### Appear
The `appear` property defines either a name of a predefined transition or a function that will be called to create a transition. The predefined transitions are:

| Name        | Description | 
| ----------  | ------------- | 
| scale      	| Scales the element in and out | 
| top      	| Translates the element in/out from the top of the screen | 
| bottom | Translates the element in/out from the bottom of the screen | 
| left | Translates the element in/out from the left of the screen | 
| right | Translates the element in/out from the right of the screen | 
| horizontal | Translates the element in/out from the left/right of the screen | 
| vertical | Translates the element in/out from the top/bottom of the screen | 
| flip | Flips the element in/out | 

[More about how to use a custom transition function](CustomTransition.md).

### Disappear
The `disappear` property of the `Transition` element is used (if not set the appear property is used) when the screen for the element is navigated from. You can use the same predefined transitions as for the `appear` property or a custom transition function.

### Inline
The `inline` property will run the defined transition inline and not create a duplicate version of the Transition View in the Transition Overlay.

### Delay
The `delay` property of the `Transition` element is used to specify that the element should be delayed when in transition. When one or more elements are delayed, their transition will start sequentially to give the impression that the different elements appear at a different time. The delay property is a true/false property.

### Anchor
The `anchor` property of the `Transition` element can be used to bind the transition to a shared element transition. Say you have an image that is transitioned in a shared transition from a list to a details screen. The details screen has a header and a box with some additional information about the image (see the ImageTransition example). If you want the header and details box to transition together with the image you can accomplish this by setting the `anchor` property to the same value as the `shared` property of the shared element. You can see an example of this in the [Image Transition example](https://github.com/fram-x/FluidTransitions/blob/develop/Examples/ImageTransition.js). 

### Animated
The `animated` property of the `Transition` element can be used to bind the interpolation driving the main transition to a property on the inner element you are rendering. This can be used to create animated components with custom animations, imagine an animated SVG transforming from one path to another, or a shape changing its apperance as the navigation transition is performed. 

To use this functionality in your own components, create a property that expects an interpolation (Animated.Value).

You can see an example of this in the [Animated Property example](https://github.com/fram-x/FluidTransitions/blob/develop/Examples/AnimatedProperty.js). 
