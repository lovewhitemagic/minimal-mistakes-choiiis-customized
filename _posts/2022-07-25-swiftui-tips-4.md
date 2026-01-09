---
title: "SwiftUI Tips 04：小型动画的最佳实践"
excerpt: "用 withAnimation 让交互更有质感。"

categories:
  - Categories4
tags:
  - [SwiftUI, Tips, Animation]

permalink: /categories4/swiftui-tips-04/

toc: true
toc_sticky: true

date: 2022-07-25
last_modified_at: 2022-07-25
---

## 要点

- 小范围动画更自然
- `withAnimation` 写在状态变更处
- 结合 `spring` 提升手感

## 示例

```swift
struct LikeButton: View {
    @State private var liked = false

    var body: some View {
        Button {
            withAnimation(.spring(response: 0.3, dampingFraction: 0.6)) {
                liked.toggle()
            }
        } label: {
            Image(systemName: liked ? "heart.fill" : "heart")
                .foregroundColor(liked ? .red : .gray)
                .scaleEffect(liked ? 1.2 : 1.0)
        }
        .padding()
    }
}
```

## 小结

动画是锦上添花，控制幅度与时长比堆特效更重要。
