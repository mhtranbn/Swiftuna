![SwiftunaLogo](/../github-media/media/swiftunaLogo.png?raw=true)

Swiftuna is a decorator library that lets any view have a cool swipe-to-reveal options menu.
Originally created for [Notebits](https://itunes.apple.com/us/app/notebits/id946399467?ls=1&mt=8).

##Example

![Swiftuna](/../github-media/media/swiftuna.gif?raw=true)

The example's source code can be found in the SwiftunaExample project.

##Installation

###Cocoapods:

Add this to your Podfile:

```ruby
pod 'Swiftuna', '~> 0.0.2'
```

###Manual installation:

1. Add this repository as a git submodule of your project. (optional)
2. Once you have downloaded the source, add the `Swiftuna.xcodeproj` as a subproject of your main project.
3. In your main project's General tab, add the `Swiftuna.framework` as an embedded framework.

Then, to use, import the `Swiftuna` framework:

```swift
import Swiftuna
```

##Usage

In order to decorate a view, the first thing to do is to instantiate a `Swiftuna` instance, which is the main decorator class. This class is in charge of doing all the configuration, so any custom attributes must be configured here. The configuration of each option in the menu is done separately in the `SwiftunaOption` class.

###Adding the menu

First, define an array of `SwiftunaOptions` to use:

```swift
let options = [
            SwiftunaOption(image: UIImage(named: "Up")!),
            SwiftunaOption(image: UIImage(named: "Down")!)
        ]
```

Each option is initialized with an image, which is what will be displayed in the menu. You can additionally change the value of the `size` property in each `SwiftunaOption` object.

The next step is to attach the menu to a view. The short version:

```swift
Swiftuna(targetView: anyView, options: options).attach()
```

If you want to customize the menu a bit, do it before the configuration is attached:

```swift
let swiftuna = Swiftuna(targetView: anyView, options: options)
swiftuna.optionsSpacing = 20
swiftuna.backgroundViewColor = UIColor.whiteColor()
swiftuna.attach()
```

###Reacting to events

In order to react to certain events (for example, when an option is selected), the listening class must implement the `SwiftunaDelegate` protocol:

```swift
class MainController: SwiftunaDelegate {
...
let swiftuna = Swiftuna(targetView: anyView, options: options)
swiftuna.delegate = self
```

Then that class must implement the following method:

```swift
func swiftuna(swiftuna: Swiftuna, didSelectOption option: SwiftunaOption, index: Int)
```

And optionally implement:

```swift
func swiftuna(swiftuna : Swiftuna, shouldDismissAfterSelectionOfOption option : SwiftunaOption, index : Int) -> Bool
```

And that it folks.

##Author

Comments and suggestions much welcome

Kevin Wong, [@kevinwl02](https://twitter.com/kevinwl02)

##License

Code distributed under the [MIT license](LICENSE)