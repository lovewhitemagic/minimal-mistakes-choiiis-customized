---
title: "SwiftUI 实战：TabView + List 组合"
excerpt: "把列表放进标签页，搭配搜索与空状态。"

categories:
  - Categories4
tags:
  - [SwiftUI, iOS, TabView, List]

permalink: /categories4/swiftui-tabview-list/

toc: true
toc_sticky: true

date: 2022-07-24
last_modified_at: 2022-07-24
---

## 目标

- 在 `TabView` 中嵌入多个 `List`
- 使用 `searchable` 增强体验
- 处理空状态提示

## 组合结构

```swift
struct RootView: View {
    @State private var keyword = ""
    @State private var selection = 0

    let items = ["SwiftUI", "UIKit", "Combine", "Xcode"]

    var filteredItems: [String] {
        guard !keyword.isEmpty else { return items }
        return items.filter { $0.localizedCaseInsensitiveContains(keyword) }
    }

    var body: some View {
        TabView(selection: $selection) {
            NavigationStack {
                List(filteredItems, id: \.self) { item in
                    Text(item)
                }
                .navigationTitle("技术栈")
                .searchable(text: $keyword, prompt: "搜索")
                .overlay {
                    if filteredItems.isEmpty {
                        ContentUnavailableView("没有结果", systemImage: "magnifyingglass")
                    }
                }
            }
            .tabItem {
                Image(systemName: "list.bullet")
                Text("列表")
            }
            .tag(0)

            Text("设置")
                .tabItem {
                    Image(systemName: "gear")
                    Text("设置")
                }
                .tag(1)
        }
    }
}
```

## 小结

`TabView` 负责结构，`List` 负责内容，`searchable` 负责查找，三者组合适合多数工具类 App。
