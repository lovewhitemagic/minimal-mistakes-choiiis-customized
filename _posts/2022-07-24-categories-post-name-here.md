---
title: "SwiftUI 01: Profile Card 만들기"
excerpt: "VStack, HStack, Image로 간단한 프로필 카드를 구성하는 방법"

categories:
  - SwiftUI
tags:
  - [swiftui, layout, ios]

permalink: /swiftui/profile-card/

toc: true
toc_sticky: true

date: 2020-05-21
last_modified_at: 2021-10-09
---

## 개요

이 글은 SwiftUI 기본 레이아웃을 연습하기 위한 프로필 카드 예제입니다.

## 핵심 포인트

- `VStack`/`HStack`으로 정보를 묶기
- `Image`에 `clipShape`와 `overlay`로 원형 아바타 만들기
- 카드 영역에 `background` + `cornerRadius` 적용

## 간단한 예시 코드

```swift
struct ProfileCard: View {
  var body: some View {
    VStack(spacing: 12) {
      Image("avatar")
        .resizable()
        .frame(width: 88, height: 88)
        .clipShape(Circle())
        .overlay(Circle().stroke(Color.white, lineWidth: 2))
      Text("Hui")
        .font(.title2).bold()
      Text("iOS / SwiftUI")
        .font(.subheadline)
        .foregroundColor(.secondary)
    }
    .padding(20)
    .background(Color(.systemBackground))
    .cornerRadius(16)
    .shadow(radius: 6)
  }
}
```
