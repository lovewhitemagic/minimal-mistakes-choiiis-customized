---
title: "SwiftUI 04: 애니메이션 기본"
excerpt: "withAnimation과 간단한 전환 효과로 UI에 생동감 더하기"

categories:
  - SwiftUI
tags:
  - [swiftui, animation, transition]

permalink: /swiftui/animation-basics/

toc: true
toc_sticky: true

date: 2022-07-24
last_modified_at: 2022-07-24
---

## 개요

SwiftUI 애니메이션은 선언적으로 사용할 수 있어 적용이 간단합니다.

## 핵심 포인트

- `withAnimation`으로 상태 변경 애니메이션 적용
- `transition`으로 뷰 등장/퇴장 효과 설정
- `animation(_:value:)`로 특정 값 변화에만 반응

## 간단한 예시 코드

```swift
struct AnimationDemo: View {
  @State private var show = false

  var body: some View {
    VStack(spacing: 16) {
      Button("Toggle") {
        withAnimation(.spring()) {
          show.toggle()
        }
      }
      if show {
        RoundedRectangle(cornerRadius: 12)
          .fill(Color.blue)
          .frame(width: 160, height: 80)
          .transition(.scale)
      }
    }
  }
}
```
