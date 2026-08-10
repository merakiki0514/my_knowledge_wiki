---
type: hub
title: "Venues"
tags: [venues, hub]
timestamp: 2026-08-10
---

# Venues

학술대회/저널별 허브. 각 venue 폴더에 `index.md`가 있고, 해당 venue의 논문으로 자동 연결됩니다.

<!-- 빌드 시 venue 슬러그 폴더 생성: venues/neurips/, venues/acl/, venues/icml/, … -->

## 빈 상태

`references.bib`가 비어 있어 venue별 폴더가 아직 없습니다.

## 예정 컨벤션

- 슬러그: 소문자, 공백은 하이픈 (`venues/ieee-tpami/`, `venues/emnlp/`)
- venue는 연도와 분리: `venue: NeurIPS`, `year: 2024` (절대 `venue: "NeurIPS 2024"`)
- 폴더 구조:
  ```
  venues/<venue-slug>/
  └── index.md   # 해당 venue 논문 목록
  ```
