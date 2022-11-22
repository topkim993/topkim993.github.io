---
layout: single
title: "UIKit Preview via SwiftUI"
---

### Step 1
- 프리뷰를 보기 위한 준비

```
#if canImport(SwiftUI) && DEBUG
import SwiftUI

public struct UIViewPreview<View: UIView>: UIViewRepresentable {
    public let view: View
    
    public init(_ builder: @escaping () -> View) {
        view = builder()
    }
    
    public func makeUIView(context: Context) -> UIView {
        return view
    }
    
    public func updateUIView(_ view: UIView, context: Context) {
        view.setContentHuggingPriority(.defaultHigh, for: .horizontal)
        view.setContentHuggingPriority(.defaultHigh, for: .vertical)
    }
}

public struct UIViewControllerPreview<ViewController: UIViewController>: UIViewControllerRepresentable {
    public func updateUIViewController(_ uiViewController: ViewController, context: Context) {
    }
    
    public let viewController: ViewController
    
    public init(_ builder: @escaping () -> ViewController) {
        viewController = builder()
    }
    
    public func makeUIViewController(context: Context) -> ViewController {
        viewController
    }
}
#endif
```

### Step 2
- UIView 프리뷰


```
#if DEBUG
import SwiftUI

struct SampleButtonPreview: PreviewProvider {
    static var previews: some View {
        UIViewPreview {
            let button = SampleButton()
            button.text = "제목"
            return button
        }
        .previewLayout(.sizeThatFits)
        .padding(10)
    }
}
#endif
```

### Step 3
- UIViewController 프리뷰

```
#if DEBUG
import SwiftUI

struct SampleViewControllerPreview: PreviewProvider {
    static var previews: some View {
        UIViewControllerPreview {
            let viewController = SampleViewController()
            return viewController
        }
        .previewLayout(.sizeThatFits)
    }
}
#endif
```
