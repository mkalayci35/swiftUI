Hi, my app swiftUI %100 [Sudeb](https://apps.apple.com/us/app/sudeb/id1494667688) 

## Navigate

- [Alert](#alert)
- [Notes](#notes)

## Alert

<img src="https://github.com/mkalayci35/swiftUI/blob/master/assets/SPAlert.png" height="350">

[SPAlert](https://github.com/ivanvorobei/SPAlert)


## Notes
## 09.03.20
Geometry Getter
``` 
struct GeometryGetter: View {
    @Binding var rect: CGRect

    var body: some View {
        GeometryReader { geometry in
            AnyView(Color.clear)
                .preference(key: RectanglePreferenceKey.self, value: geometry.frame(in: .global))
        }.onPreferenceChange(RectanglePreferenceKey.self) { (value) in
            self.rect = value
            print(self.rect)
        }
    }
}

struct RectanglePreferenceKey: PreferenceKey {
    static var defaultValue: CGRect = .zero

    static func reduce(value: inout CGRect, nextValue: () -> CGRect) {
        value = nextValue()
    }
}

```
Using  Geometry Getter
```
@State private var detail: CGRect = .zero

VStack {
    Text("Good Morning Istanbul")
}
.background(GeometryGetter(rect: self.$detail))
```
### How to resolve: 'keyWindow' was deprecated in iOS 13.0

``` 
var screenStatusBarHeight: CGFloat {
    let window = UIApplication.shared.windows.filter {$0.isKeyWindow}.first
    return (window?.windowScene?.statusBarManager?.statusBarFrame.height)!
}
```
## 10.03.20
Turn screen off when swiping right
``` 
.gesture(
                DragGesture()
                    .onChanged { item in
                        if item.startLocation.x - item.location.x < -50 {
                            self.presentationMode.wrappedValue.dismiss()
                        }
                }
        )
```
Used dismiss
```
@Environment(\.presentationMode) var presentationMode
```
