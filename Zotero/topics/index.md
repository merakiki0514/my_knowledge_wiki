---
type: hub
title: "Topics"
tags: [topics, hub]
timestamp: 2026-08-10
---

# Topics

태그 기반 주제 허브.

<!-- 빌드 시 태그 폴더 생성: topics/synthetic_data/, topics/llm_alignment/, … -->

## 빈 상태

`references.bib`가 비어 있어 주제별 폴더가 아직 없습니다.

## 예정 컨벤션

- 폴더명: 소문자 + 언더스코어 (`topics/synthetic_data/`, `topics/llm_alignment/`)
- 태그 정규화 규칙: 공백 → `_`, 영문 대문자 → 소문자
- 각 폴더의 `index.md`는 해당 태그를 가진 논문 + 관련 태그(공출현 빈도 기반)
