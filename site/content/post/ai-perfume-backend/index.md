---
title: "AI 기반 향수 추천 쇼핑몰 백엔드 API 개발"
description: "감성 키워드와 설문, 자유 텍스트를 바탕으로 향수를 추천하는 쇼핑몰의 백엔드 API를 개발한 팀 프로젝트 기록입니다."
slug: "ai-perfume-backend"
date: 2026-11-02
categories:
    - 프로젝트
tags:
    - Django
    - AI 추천
    - 백엔드
---

## 활동 개요

- **유형**: 팀 프로젝트 (백엔드 담당)
- **주제**: 사용자의 감성 키워드, 선호 분위기, 사용 목적을 기반으로 향수를 추천하는 AI·설문 추천 쇼핑몰 웹사이트

---

## 활동 목적

사용자가 향수를 직접 고르기 어렵다는 문제를 해결하기 위해, 로그인 후 설문에 답하거나 AI 검색창에 선호 분위기와 사용 목적을 자유롭게 입력하면 맞춤 향수를 추천받을 수 있는 서비스를 만들고자 했습니다.

---

## 구현 사항

- Django REST Framework 기반 상품, 추천, 회원 관련 API 구현
- 자유 텍스트를 입력하면 AI가 향수를 추천해 주는 API 개발 (Clova Studio 사용)
- 감성 키워드·설문 기반 향수 추천 API 개발 (scikit-learn, sentence-transformers, pandas)
- 추천 결과 API와 추천 사유 API를 분리 설계하여 프론트엔드에서 통합 조회할 수 있도록 구조화
- NCP Object Storage 연동을 통한 상품 이미지 관리 및 CSV 데이터 일괄 업로드
- NCP와 Docker Compose를 사용한 배포 및 배포 자동화 구현
