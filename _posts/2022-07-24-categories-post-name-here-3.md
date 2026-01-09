---
title: "SwiftUI 03: 상태 관리 @State와 @Binding"
excerpt: "부모-자식 뷰에서 상태를 전달하고 변경하는 기본 패턴"

categories:
  - SwiftUI
tags:
  - [swiftui, state, binding]

permalink: /swiftui/state-binding/

toc: true
toc_sticky: true

date: 2022-07-24
last_modified_at: 2022-07-24
---

## 개요

상태 관리의 기본은 `@State`와 `@Binding`입니다.

## 핵심 포인트

- 부모 뷰에서 `@State`로 상태 소유
- 자식 뷰로 `@Binding` 전달
- 버튼 액션으로 상태 변경

## 간단한 예시 코드

```swift
struct ParentView: View {
  @State private var isOn = false

  var body: some View {
    Toggle("알림", isOn: $isOn)
    ChildView(isOn: $isOn)
  }
}

struct ChildView: View {
  @Binding var isOn: Bool

  var body: some View {
    Button(isOn ? "끄기" : "켜기") {
      isOn.toggle()
    }
  }
}
```
