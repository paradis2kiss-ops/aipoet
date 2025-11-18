# 인공지능 시인 (AI Poet)

LangChain과 OpenAI GPT를 활용한 한국어 시 생성 웹 애플리케이션입니다.

## 프로젝트 개요

이 프로젝트는 Streamlit 프레임워크를 기반으로 하며, OpenAI의 GPT-4o-mini 모델을 사용하여 사용자가 입력한 주제에 대한 한국어 시를 자동으로 생성합니다.

## 주요 기능

- **사용자 친화적 인터페이스**: Streamlit을 통한 직관적인 웹 UI 제공
- **API 키 보안**: 사이드바를 통한 안전한 API 키 입력
- **실시간 시 생성**: GPT-4o-mini 모델을 활용한 즉각적인 시 작성
- **에러 처리**: 상세한 에러 메시지 및 사용자 가이드 제공

## 기술 스택

### 주요 라이브러리
- **Streamlit** (>=1.32.0): 웹 애플리케이션 프레임워크
- **LangChain** (>=0.2.0): LLM 애플리케이션 개발 프레임워크
- **LangChain-OpenAI** (>=0.1.0): OpenAI 모델 통합
- **OpenAI** (>=1.30.0): OpenAI API 클라이언트
- **Python-dotenv** (>=1.0.1): 환경 변수 관리

## 설치 방법

### 1. 저장소 클론 (또는 파일 다운로드)

```bash
# 프로젝트 디렉토리로 이동
cd your-project-directory
```

### 2. 가상환경 생성 및 활성화 (권장)

```bash
# 가상환경 생성
python -m venv venv

# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

### 3. 필요한 패키지 설치

```bash
pip install -r requirements.txt
```

## 사용 방법

### 1. OpenAI API 키 준비

- [OpenAI Platform](https://platform.openai.com/)에서 API 키 발급
- API 키는 `sk-`로 시작합니다

### 2. 애플리케이션 실행

```bash
streamlit run app.py
```

### 3. 웹 브라우저에서 사용

1. 브라우저가 자동으로 열립니다 (기본: http://localhost:8501)
2. **사이드바**에서 OpenAI API 키 입력
3. **메인 화면**에서 시의 주제 입력
4. **"시 작성 요청하기"** 버튼 클릭
5. AI가 생성한 시 확인

## 프로젝트 구조

```
project/
│
├── app.py              # 메인 애플리케이션 파일
├── requirements.txt    # 패키지 의존성 목록
└── README.md          # 프로젝트 문서 (이 파일)
```

## 코드 주요 구성 요소

### 1. API 키 관리
```python
with st.sidebar:
    st.header("설정")
    api_key = st.text_input("OpenAI API Key를 입력하세요:", type="password")
```

### 2. LangChain 파이프라인
```python
llm = init_chat_model("gpt-4o-mini", model_provider="openai")
prompt = ChatPromptTemplate.from_messages([...])
chain = prompt | llm | output_parser
```

### 3. 시 생성 요청
```python
result = chain.invoke({"input": f"{content}에 대한 아름다운 시를 써 줘"})
```

## 에러 처리

애플리케이션은 다음과 같은 에러 상황을 처리합니다:

- API 키 미입력
- 주제 미입력
- API 키 오류
- 네트워크 오류
- 기타 예외 상황

## 주의사항

1. **API 키 보안**: API 키를 공개 저장소에 커밋하지 마세요
2. **API 사용량**: OpenAI API 사용에 따른 과금이 발생할 수 있습니다
3. **인터넷 연결**: 애플리케이션 실행 시 인터넷 연결이 필요합니다

## 개발 환경

- Python 3.8 이상 권장
- Windows, macOS, Linux 지원

## 라이선스

이 프로젝트는 교육 목적으로 작성되었습니다.

## 문제 해결

### API 키 오류
- API 키가 올바른지 확인
- OpenAI 계정의 크레딧 잔액 확인

### 패키지 설치 오류
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### 포트 충돌 오류
```bash
streamlit run app.py --server.port 8502
```

## 향후 개선 사항

- [ ] 시의 스타일 선택 기능 추가
- [ ] 생성된 시 저장 기능
- [ ] 다양한 LLM 모델 선택 옵션
- [ ] 시 생성 히스토리 관리
- [ ] 시 평가 및 피드백 기능

## 참고 자료

- [Streamlit 공식 문서](https://docs.streamlit.io/)
- [LangChain 공식 문서](https://python.langchain.com/)
- [OpenAI API 문서](https://platform.openai.com/docs/)

---

**개발자**: 미밍
**마지막 업데이트**: 2025년 11월
