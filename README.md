## Navigate

- [Alert](#alert)

## Alert

<img src="https://github.com/mkalayci35/swiftUI/blob/master/assets/SPAlert.png" height="350">

[SPAlert](https://github.com/ivanvorobei/SPAlert)

#09.03.20
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
