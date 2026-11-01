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

---

## 본인 역할 및 기여

팀 프로젝트에서 **백엔드를 담당**했습니다. 프론트엔드와 협업하며 아래 작업을 맡았습니다.

- **AI 추천 로직 개발**
  1. 사용자가 텍스트를 입력하면 AI가 추천 사유, 설명, 노트 키워드를 생성
  2. DB에서 일치하는 노트를 가진 향수 5가지를 추천
  3. 일치하는 향수가 없으면 무작위로 5개를 추천
- **상품 데이터 추가**: 향수 목(mock) 데이터를 CSV로 만들고 Object Storage를 사용해 상품 데이터를 관리
- **서버 환경 구성**: NCP(Naver Cloud Platform)와 Docker Compose 기반 개발·배포 환경 구성 (Django, PostgreSQL, Redis, Celery, Nginx, Gunicorn)
- **인증·보안**: JWT와 SimpleJWT 기반 인증 구조 설계, 카카오 소셜 로그인 연동 테스트

---

## 기술 스택

Python, Django REST Framework, PostgreSQL, Redis, Celery, NCP(Naver Cloud Platform), Object Storage, Clova Studio, JWT, Docker, scikit-learn, sentence-transformers, pandas

---

## 기술 선정 이유

| 기술 | 선정 이유 |
|------|-----------|
| **DRF** | 빠르고 일관성 있게 REST API를 개발하기 위해 사용 |
| **sentence-transformers** | 사용자의 감성 키워드를 의미 단위로 임베딩해 텍스트 기반 추천 정확도를 높이기 위해 선정 |
| **scikit-learn** | 설문 응답 데이터를 벡터화하고 유사도 기반 추천 알고리즘을 빠르게 실험하기 위해 선정 |
| **Redis + Celery** | 배너 API 같은 반복 조회 요청을 캐싱해 DB 부하를 줄이고, 메모리 기반의 빠른 응답 속도로 사용자 경험을 개선하기 위해 도입 |
| **Object Storage** | 대량의 상품 이미지 관리와 확장성을 고려해 선택 |
| **Docker Compose** | 팀 단위 개발과 배포 환경의 일관성을 위해 사용 |
