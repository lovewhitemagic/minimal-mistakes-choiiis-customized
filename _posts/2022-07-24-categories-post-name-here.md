---
title: "SwiftUI 入门：TabView 基础用法"
excerpt: "用最小代码搭建底部标签页，理解 selection、标签与图标。"

categories:
  - Categories1
tags:
  - [SwiftUI, iOS, TabView]

permalink: /categories1/swiftui-tabview/

toc: true
toc_sticky: true

date: 2022-07-24
last_modified_at: 2022-07-24
---

## 目标

- 用 `TabView` 实现底部标签页
- 了解 `selection` 与 `tag` 的配合
- 自定义图标与标题

## 最小示例

```swift
import SwiftUI

struct ContentView: View {
    @State private var selection = 0

    var body: some View {
        TabView(selection: $selection) {
            Text("首页")
                .tabItem {
                    Image(systemName: "house")
                    Text("首页")
                }
                .tag(0)

            Text("收藏")
                .tabItem {
                    Image(systemName: "star")
                    Text("收藏")
                }
                .tag(1)
        }
    }
}
```

## 关键点

- `selection` 绑定当前选中的标签页
- 每个页面用 `.tag` 对应一个唯一值
- 图标来自 SF Symbols，常用 `systemName`

## 小结

`TabView` 是 SwiftUI 中实现底部导航的首选组件。先把结构搭起来，再考虑嵌入 `NavigationStack` 或 `List`。
