---
title: "SwiftUI 进阶：List + NavigationStack"
excerpt: "在列表中导航到详情页，并理解路径与状态。"

categories:
  - Categories3
tags:
  - [SwiftUI, iOS, NavigationStack]

permalink: /categories3/swiftui-list-navigation/

toc: true
toc_sticky: true

date: 2022-07-24
last_modified_at: 2022-07-24
---

## 目标

- 在 `List` 中使用 `NavigationStack`
- 通过 `NavigationLink` 跳转详情页
- 使用模型驱动导航

## 数据模型

```swift
struct Article: Identifiable, Hashable {
    let id = UUID()
    let title: String
    let summary: String
}

let articles = [
    Article(title: "TabView 基础", summary: "底部导航的关键点"),
    Article(title: "List 基础", summary: "数组渲染与分组"),
    Article(title: "NavigationStack", summary: "新式导航容器")
]
```

## 列表 + 详情

```swift
NavigationStack {
    List(articles) { article in
        NavigationLink(value: article) {
            VStack(alignment: .leading, spacing: 4) {
                Text(article.title).font(.headline)
                Text(article.summary).font(.subheadline).foregroundColor(.secondary)
            }
        }
    }
    .navigationTitle("教程")
    .navigationDestination(for: Article.self) { article in
        VStack(alignment: .leading, spacing: 12) {
            Text(article.title).font(.title)
            Text(article.summary)
        }
        .padding()
    }
}
```

## 小结

使用 `NavigationStack` 和 `navigationDestination` 可以让导航状态更清晰，尤其适合复杂层级。
