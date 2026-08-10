---
type: index
title: "Research Wiki — Home"
tags: [wiki, okf]
timestamp: 2026-08-10
---

# Research Wiki

OKF(Open Knowledge Format) 기반 연구용 위키. Obsidian에서 열어서 사용.

## 들어가기

- [[log|변경 로그 (log.md)]] — 빌드/업데이트 이력
- [[papers/index|논문 목록 (papers/)]] — 모든 논문 페이지, 최신순

## 허브

| 분류 | 진입점 | 설명 |
| --- | --- | --- |
| Venue | [[venues/index]] | 학술대회/저널별 묶음 (예: NeurIPS, ACL, ICML) |
| Year | [[years/index]] | 출판연도별 묶음 (2026, 2025, …) |
| Author | [[authors/index]] | 저자별 묶음 |
| Topic | [[topics/index]] | 태그 기반 주제 허브 (예: `synthetic_data`) |

## 컨벤션

- **태그**: 소문자 + 언더스코어 (`synthetic_data`, `llm_alignment` 등)
- **Venue와 Year 분리**: `venue = "NeurIPS"`, `year = 2024` — 합치지 않음
- **프런트매터**: 모든 논문 페이지는 `type`, `title`, `tags`, `timestamp` 포함
- **Summary**: 각 논문 페이지 맨 위 한 문단. Abstract 기반, 없으면 제목+메타데이터로 생성
- **링크**: Obsidian wikilink `[[paper-slug]]` 사용

## 상태

> `references.bib`가 비어 있어 논문 페이지가 아직 없습니다.
> Zotero에서 BibLaTeX으로 내보내 `references.bib`를 채우면 자동으로 페이지가 생성됩니다.
