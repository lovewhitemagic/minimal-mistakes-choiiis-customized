---
title: "SwiftUI 02: List + NavigationStack 기초"
excerpt: "목록 화면에서 상세 화면으로 이동하는 기본 흐름 정리"

categories:
  - SwiftUI
tags:
  - [swiftui, list, navigation]

permalink: /swiftui/list-navigation/

toc: true
toc_sticky: true

date: 2022-07-24
last_modified_at: 2022-07-24
---

## 개요

SwiftUI에서 가장 자주 쓰이는 패턴은 목록 → 상세 화면 이동입니다.

## 핵심 포인트

- `NavigationStack` 안에서 `List` 사용
- `NavigationLink`로 상세 화면 연결
- `Identifiable` 모델로 리스트 관리

## 간단한 예시 코드

```swift
struct Book: Identifiable {
  let id = UUID()
  let title: String
}

struct BookListView: View {
  let books = [Book(title: "SwiftUI Cookbook"), Book(title: "Layout Tips")]

  var body: some View {
    NavigationStack {
      List(books) { book in
        NavigationLink(book.title) {
          Text(book.title)
            .font(.title)
        }
      }
      .navigationTitle("Books")
    }
  }
}
```
