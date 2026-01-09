---
title: "SwiftUI 入门：List 基础与样式"
excerpt: "用 List 渲染数组、分组与行内布局。"

categories:
  - Categories2
tags:
  - [SwiftUI, iOS, List]

permalink: /categories2/swiftui-list/

toc: true
toc_sticky: true

date: 2022-07-24
last_modified_at: 2022-07-24
---

## 目标

- 用 `List` 显示数据集合
- 了解 `List` 的行内布局
- 使用 `Section` 做分组

## 基础数据

```swift
struct Fruit: Identifiable {
    let id = UUID()
    let name: String
    let color: Color
}

let fruits = [
    Fruit(name: "苹果", color: .red),
    Fruit(name: "香蕉", color: .yellow),
    Fruit(name: "蓝莓", color: .blue)
]
```

## 基本 List

```swift
List(fruits) { fruit in
    HStack {
        Circle()
            .fill(fruit.color)
            .frame(width: 12, height: 12)
        Text(fruit.name)
    }
}
```

## 分组示例

```swift
List {
    Section("常见水果") {
        ForEach(fruits) { fruit in
            Text(fruit.name)
        }
    }
}
```

## 小结

`List` 默认支持滚动与分隔线，搭配 `Section` 可以快速做出清晰的信息结构。
