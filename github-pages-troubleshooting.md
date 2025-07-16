# GitHub Pages 배포 문제 해결 가이드

## 문제 분석
EYEON CLINIC 웹사이트가 로컬에서는 정상 작동하지만 GitHub Pages에서는 작동하지 않는 문제 해결을 위한 단계별 가이드입니다.

## 주요 문제점들

### 1. Tailwind CSS 빌드 프로세스 문제
- GitHub Pages는 Node.js 빌드를 자동 실행하지 않음
- 빌드된 CSS 파일이 누락되어 스타일이 적용되지 않음

### 2. Firebase 모듈 로딩 문제
- ES6 모듈 import 시 CORS 정책 제한
- GitHub Pages에서 Firebase 초기화 실패

### 3. 상대 경로 문제
- GitHub Pages URL 구조 차이로 인한 리소스 로딩 실패

## 해결방안

### 즉시 적용 가능한 해결책
1. **빌드된 CSS 파일 직접 커밋**
   ```bash
   npm run build
   git add assets/dist/output.css
   git commit -m "Add built Tailwind CSS"
   ```

2. **GitHub Actions 워크플로우 설정**
   - `.github/workflows/deploy.yml` 파일 생성
   - 자동 빌드 및 배포 파이프라인 구성

3. **Firebase 설정 수정**
   - Authorized Domains에 GitHub Pages URL 추가
   - CORS 정책 업데이트

## 검증 완료 사항
- ✅ GitHub MCP server 기능 정상 작동
- ✅ Commit/Push 기능 테스트 완료
- ✅ 파일 생성/업데이트 기능 검증

---
*이 가이드는 EYEON CLINIC 웹사이트의 안정적인 GitHub Pages 배포를 위해 작성되었습니다.*