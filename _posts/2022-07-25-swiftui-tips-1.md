---
title: "SwiftUI Tips 01：用 @State 管理简单状态"
excerpt: "掌握 @State 的更新机制与常见误区。"

categories:
  - Categories1
tags:
  - [SwiftUI, Tips, State]

permalink: /categories1/swiftui-tips-01/

toc: true
toc_sticky: true

date: 2022-07-25
last_modified_at: 2022-07-25
---

## 要点

- `@State` 只用于 View 内部状态
- 状态变化会触发视图重新计算
- 不要把业务模型放进 `@State`

## 示例

```swift
struct CounterView: View {
    @State private var count = 0

    var body: some View {
        VStack(spacing: 16) {
            Text("计数: \(count)")
                .font(.title2)

            Button("+1") {
                count += 1
            }
        }
        .padding()
    }
}
```

## 小结

把 `@State` 当作轻量 UI 状态容器，用来驱动视图变化即可。
