---
title: "대학생 AI 스마트 어시스턴트: Gmail 및 학사 일정 자동화 에이전트"
description: "Gemini LLM과 GitHub Actions를 활용해 Gmail 요약, 캘린더 일정 등록, 전북대 장학 공지 크롤링 및 라이트너 복습 퀴즈를 자동화한 개인 프로젝트입니다."
slug: "college-ai-agent"
date: 2026-10-30
categories:
    - 프로젝트
tags:
    - Python
    - AI 에이전트
    - 자동화
    - GitHub Actions
---

## 활동 개요

- **수행 기간**: 2026년 10월 ~ 2026년 11월
- **상태**: 완료 (운영 중)
- **유형**: 개인 프로젝트 (1인 단독 기획·개발)
- **저장소**: [Gmail-Agent (GitHub)](https://github.com/kyukyu300/Gmail-Agent)

---

## 활동 목적

대학 생활 중 쏟아지는 수많은 Gmail 안내 메일, 전북대학교 학사·장학 공지사항, 과제 마감 및 시험 일정을 매일 일일이 확인하고 캘린더에 수동 등록하는 데 많은 시간과 피로가 소모되었습니다. 

이 문제를 해결하기 위해, **별도의 유료 서버 비용 없이 클라우드 환경에서 매일 아침 구동되어 중요 정보 요약, 일정 자동 등록, 전공·취업 퀴즈 투표를 자동으로 브리핑해주는 서버리스 AI 에이전트**를 구축하고자 했습니다.

---

## 본인 역할 및 기여

**개인 프로젝트**로 기획부터 데이터 수집, LLM 연동, 클라우드 자동화 배포까지 전 과정을 직접 수행했습니다.

- **Google API 연동**: Gmail API를 활용한 최근 24시간 미확인 메일 수집 및 Google Calendar API를 통한 마감일 자동 이벤트 등록
- **전북대학교 공지 크롤러 개발**: BeautifulSoup를 활용해 교내 일반 공지와 장학 공지 목록을 정기 크롤링하고 장학금/근로학생 혜택 키워드 필터링 로직 구현
- **Gemini LLM 기반 의사결정 파이프라인 설계**: 긴 이메일과 공지 본문을 3줄 핵심 요약하고, 텍스트 내 시험/과제 마감 날짜를 파싱하는 프롬프트 엔지니어링 수행
- **에빙하우스 망각 곡선 기반 라이트너(Leitner) 퀴즈 시스템**: 텔레그램 네이티브 Quiz Poll을 발송하고, 전날 투표 결과를 읽어 오답은 당일 복습, 정답은 주기(1일 → 3일 → 7일) 승급하는 로직 개발
- **GitHub Actions 기반 서버리스 운영**: 24시간 가동 서버 대신 cron 스케줄러를 활용하고, 퀴즈 상태 DB(`quiz_db.json`)를 실행 직후 GitHub에 자동 커밋·푸시하는 상태 영구 보존(State Persistence) 아키텍처 구축

---

## 기술 스택

Python, Google Gemini API, Gmail API, Google Calendar API, Telegram Bot API, BeautifulSoup4, GitHub Actions (Cron Scheduler), Git (State Persistence)

---

## 기술 선정 이유

| 기술 | 선정 이유 |
|------|-----------|
| **Gemini Flash-Lite** | 대량의 이메일 및 공지사항 텍스트를 빠르고 경제적인 비용으로 요약·파싱하기 위해 채택 |
| **Google API (Gmail/Calendar)** | 공식 OAuth 2.0 라이브러리를 통해 안전한 권한 획득 및 캘린더 자동 등록 연동 용이 |
| **Telegram Bot API** | 별도 프론트엔드 웹앱 구축 없이 스마트폰 네이티브 푸시 알림과 인터랙티브 퀴즈 투표 UI를 즉시 활용할 수 있어 선정 |
| **GitHub Actions (스케줄러)** | 24시간 유료 클라우드 인스턴스를 유지할 필요 없이 매일 아침 정해진 시간(08:48 KST)에 컨테이너를 구동하고 종료할 수 있어 서버 비용 제로화 달성 |
| **Git 기반 상태 동기화** | 외부 RDBMS 없이 `quiz_db.json`을 실행 종료 시마다 커밋·푸시하여 학습 이력을 안전하게 무료로 보존 |
