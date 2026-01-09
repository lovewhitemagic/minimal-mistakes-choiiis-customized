---
title: "SwiftUI Tips 02：用 @Binding 传递可变状态"
excerpt: "父子视图共享状态的最简单方式。"

categories:
  - Categories2
tags:
  - [SwiftUI, Tips, Binding]

permalink: /categories2/swiftui-tips-02/

toc: true
toc_sticky: true

date: 2022-07-25
last_modified_at: 2022-07-25
---

## 要点

- `@Binding` 只是引用，不拥有数据
- 子视图修改会同步到父视图
- 常用于表单或开关控件

## 示例

```swift
struct SettingsView: View {
    @State private var isOn = false

    var body: some View {
        ToggleRow(isOn: $isOn)
            .padding()
    }
}

struct ToggleRow: View {
    @Binding var isOn: Bool

    var body: some View {
        Toggle("启用通知", isOn: $isOn)
    }
}
```

## 小结

父视图负责数据，子视图负责交互，用 `@Binding` 连接即可。
