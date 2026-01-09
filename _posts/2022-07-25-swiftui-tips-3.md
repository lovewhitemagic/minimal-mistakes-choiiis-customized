---
title: "SwiftUI Tips 03：List 的空状态处理"
excerpt: "无数据时的体验细节决定专业度。"

categories:
  - Categories3
tags:
  - [SwiftUI, Tips, List]

permalink: /categories3/swiftui-tips-03/

toc: true
toc_sticky: true

date: 2022-07-25
last_modified_at: 2022-07-25
---

## 要点

- `List` 空数组不会显示任何行
- 用 `overlay` 或 `contentUnavailable` 提示
- 提示文案要清晰且短

## 示例

```swift
struct EmptyListView: View {
    let items: [String]

    var body: some View {
        List(items, id: \.self) { item in
            Text(item)
        }
        .overlay {
            if items.isEmpty {
                ContentUnavailableView("暂无数据", systemImage: "tray")
            }
        }
    }
}
```

## 小结

空状态不是异常，而是正常场景，应该显式设计。
