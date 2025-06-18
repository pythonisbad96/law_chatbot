<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>생활법령 기반 RAG 챗봇</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      line-height: 1.6;
      background-color: #ffffff;
      color: #1a1a1a;
      max-width: 900px;
      margin: 40px auto;
      padding: 0 20px;
    }
    h1, h2 {
      color: #007acc;
    }
    pre {
      background: #f3f3f3;
      padding: 10px;
      border-radius: 5px;
      overflow-x: auto;
    }
    code {
      font-family: Consolas, monospace;
    }
    ul {
      margin-left: 20px;
    }
    hr {
      margin: 30px 0;
      border: none;
      border-top: 1px solid #ccc;
    }
  </style>
</head>
<body>

  <h1>📘 생활법령 기반 RAG 챗봇</h1>

  <hr>

  <h2>🧠 프로젝트 개요</h2>
  <p>
    이 프로젝트는 생활법령 NT 기반 데이터를 활용하여 유사 조문을 검색하고,
    LLM(Groq LLaMA3 또는 KoGPT)으로 자연스러운 답변을 생성하는
    RAG 기반 한국어 법률 챗봇입니다.
  </p>

  <hr>

  <h2>📁 폴더 구성</h2>
  <ul>
    <li><code>app.py</code>: Flask 기반 서버 코드</li>
    <li><code>templates/chat.html</code>: iMessage 스타일 채팅 UI</li>
    <li><code>create_chunks_and_embeddings.py</code>: 문장 단위 청크 + KoSBERT 임베딩 생성</li>
    <li><code>build_faiss_index.py</code>: FAISS 벡터 인덱스 구축</li>
    <li><code>항_조문텍스트.csv</code>: RDF 조문 텍스트 정리 파일</li>
  </ul>

  <hr>

  <h2>⚙️ 실행 순서</h2>
  <ol>
    <li><strong>KoSBERT 청크 임베딩 생성</strong>
      <pre><code>python create_chunks_and_embeddings.py</code></pre>
    </li>
    <li><strong>FAISS 인덱스 생성</strong>
      <pre><code>python build_faiss_index.py</code></pre>
    </li>
    <li><strong>Flask 앱 실행</strong>
      <pre><code>$env:FLASK_APP = "app.py"
flask run</code></pre>
    </li>
  </ol>

  <hr>

  <h2>🎨 주요 기능</h2>
  <ul>
    <li>💬 질문에 대한 조문 검색 + LLM 요약</li>
    <li>📌 한국어-only 응답 필터링</li>
    <li>🗨️ iMessage 스타일 채팅 UI</li>
    <li>🔄 대화 누적 (멀티턴)</li>
    <li>🧹 불필요한 토큰(nn, nsn) 제거 및 정리</li>
  </ul>

  <hr>

  <h2>🛠 수정 요청 히스토리</h2>
  <ul>
    <li>✅ iMessage 스타일 UI로 변경 요청</li>
    <li>✅ Groq 응답에서 외국어 제거 필터 추가</li>
    <li>✅ 'nn', 'n', 'nsn' 같은 불필요한 토큰 제거</li>
    <li>✅ 멀티턴 대화 누적 오류 해결 (scroll 유지 포함)</li>
    <li>✅ 대화가 누적되지 않던 문제 → session 유지 구조 확인</li>
    <li>✅ 문장 자르기 개선 → NLTK 기반 정확한 청크 생성 방식 적용</li>
    <li>✅ HTML README가 GitHub에서 깨져 보여서 Markdown 변환 요청</li>
    <li>✅ 사용자 질문 앞뒤 응답 이상 문제 → 프롬프트 및 필터 보완</li>
  </ul>

  <hr>

  <h2>📝 향후 개선 아이디어</h2>
  <ul>
    <li>🧠 KoGPT API 또는 KorLLM 로컬 버전 교체</li>
    <li>📁 대화 로그 저장 (txt, csv, pdf)</li>
    <li>⏱️ 응답 시간, 날짜 출력</li>
    <li>📲 모바일 최적화 및 다크모드</li>
  </ul>

</body>
</html>

