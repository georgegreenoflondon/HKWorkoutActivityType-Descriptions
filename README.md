# HKWorkoutActivityType-Descriptions
A simple HKWorkoutActivityType extension to map the various available types to human readable and user friendly strings.

HKWorkoutActivityType contains many useful values for determining differently workouts, but since it is a `UInt` based `enum` there is no easy way to convert these to user friendly representations. With this extension you can now convert these types into simple common names, or even to appropriate emoji representations, where available.

## Examples

```
let type: HKWorkoutActivityType = .americanFootball

type.name             // "American Football"
type.commonName       // "American Football"
type.associatedEmoji  // "🏈"
```

For most activity types the `name` and `commonName` are the same, however there are a few examples (actually 1 at the time of writing), that can make use of these two names:

```
let type: HKWorkoutActivityType = .highIntensityIntervalTraining

type.name             // "High Intensity Interval Training"
type.commonName       // "HIIT"
```

Also, while many of the common sport types, such as American Football above, have a simple gender-neutral emoji representation, for some there is not. So there is an additional helper function to allow these to be converted:

```
let type: HKWorkoutActivityType = .running

type.associatedEmoji(for: .female)    // "🏃‍♀️"
type.associatedEmoji(for: .male)      // "🏃‍♂️"
```

For those that do not have gender specific representations, this function will return the value of `associatedEmoji`. For some activity types I was unable to determine an appropriate emoji representation, so these simply return `nil`.
