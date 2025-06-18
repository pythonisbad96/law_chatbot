# 📘 생활법령 기반 RAG 챗봇

---

## 🧠 프로젝트 개요

이 프로젝트는 생활법령 NT 기반 데이터를 활용하여 유사 조문을 검색하고,  
LLM(Groq LLaMA3 또는 KoGPT)으로 자연스러운 답변을 생성하는  
RAG 기반 한국어 법률 챗봇입니다.

---

## 📁 폴더 구성

- `app.py`: Flask 기반 서버 코드  
- `templates/chat.html`: iMessage 스타일 채팅 UI  
- `create_chunks_and_embeddings.py`: 문장 단위 청크 + KoSBERT 임베딩 생성  
- `build_faiss_index.py`: FAISS 벡터 인덱스 구축  
- `항_조문텍스트.csv`: RDF 조문 텍스트 정리 파일  

---

## ⚙️ 실행 순서

1. **KoSBERT 청크 임베딩 생성**

    ```bash
    python create_chunks_and_embeddings.py
    ```

2. **FAISS 인덱스 생성**

    ```bash
    python build_faiss_index.py
    ```

3. **Flask 앱 실행**

    ```bash
    $env:FLASK_APP = "app.py"
    flask run
    ```

---

## 🎨 주요 기능

- 💬 질문에 대한 조문 검색 + LLM 요약  
- 📌 한국어-only 응답 필터링  
- 🗨️ iMessage 스타일 채팅 UI  
- 🔄 대화 누적 (멀티턴)  
- 🧹 불필요한 토큰(nn, nsn) 제거 및 정리  

---

## 🛠 수정 요청 히스토리

- ✅ iMessage 스타일 UI로 변경 요청  
- ✅ Groq 응답에서 외국어 제거 필터 추가  
- ✅ 'nn', 'n', 'nsn' 같은 불필요한 토큰 제거  
- ✅ 멀티턴 대화 누적 오류 해결 (scroll 유지 포함)  
- ✅ 대화가 누적되지 않던 문제 → session 유지 구조 확인  
- ✅ 문장 자르기 개선 → NLTK 기반 정확한 청크 생성 방식 적용  
- ✅ HTML README가 GitHub에서 깨져 보여서 Markdown 변환 요청  
- ✅ 사용자 질문 앞뒤 응답 이상 문제 → 프롬프트 및 필터 보완  

---

## 📝 향후 개선 아이디어

- 🧠 KoGPT API 또는 KorLLM 로컬 버전 교체  
- 📁 대화 로그 저장 (txt, csv, pdf)  
- ⏱️ 응답 시간, 날짜 출력  
- 📲 모바일 최적화 및 다크모드  

