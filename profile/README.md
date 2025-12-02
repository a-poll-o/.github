## Scentra: 생성형 AI 기반 향수 쇼핑 플랫폼 🥀

<p align="center">
<img width="700px" height="auto" alt="스크린샷 2025-11-21 오후 5 50 52" src="https://github.com/user-attachments/assets/99944d68-5d39-4654-9351-6602a2410e8c" />
</p>

<b>"Scent(향)"</b>과 <b>"Central(중심)"</b>의 합성어로, 모든 향과 관련된 개인 맞춤형 서비스가 중심이 되는 플랫폼
- 생성형 AI 기반으로 향을 시각화하고, 사용자의 취향에 맞는 개인 맞춤형 추천 서비스를 제공하는 향수 쇼핑 플랫폼

<br>

## 🧑‍💻 팀원
<table width="100%">
  <tr>
    <th>팀장</th>
    <th>개발</th>
    <th>개발</th>
    <th>개발</th>
    <th>디자인</th>
  </tr>
  <tr>
    <td>최아영</td>
    <td>이수민</td>
    <td>이영서</td>
    <td>이효민</td>
    <td>양찬미</td>
  </tr>
  <tr>
    <td>풀스택, 이미지 생성 AI</td>
    <td>풀스택, LLM</td>
    <td>풀스택, 이미지 생성 AI</td>
    <td>풀스택, LLM</td>
    <td>UI/UX 디자인</td>
  </tr>
</table>

<br>

## 🍿 기술 스택
<p align="center">
<img width="352" height="353" alt="스크린샷 2025-12-02 오후 3 56 44" src="https://github.com/user-attachments/assets/4552ed13-d3b5-4e7e-a4b8-9708d312450c" />
</p>

- **AI 모델 활용**
  <div></div>
  
  Huggin Face Hub의 오픈소스 [**Stable Diffusion 3.5 large**](https://huggingface.co/stabilityai/stable-diffusion-3.5-large)와 Open AI [**GPT-4o-mini**](https://openai.com/ko-KR/index/openai-api/) 모델을 활용
- **CI/CD**
  <div></div>
  
   Github Actions를 이용한 자동화된 빌드, 테스트, 배포 파이프라인 구성
- **클라우드 인프라**
  <div></div>
  
   AWS 기반 클라우드 환경에서 EC2를 활용한 서버 구축 및 운영, RDS를 통한 관계형 데이터베이스 관리, S3를 이용한 이미지 데이터 저장 및 관리

<br>

<h2>🛍️ 기획 배경</h2>
<div>
  <b>온라인</b>
  <ul>
    <li>직관적이지 않은 상품 대표 이미지</li>
    <li>향의 직접 경험 부족</li>
  </ul>
  <b>오프라인</b>
  <ul>
    <li>매장 접근성 문제</li>
    <li>제한된 브랜드 및 제품</li>
  </ul>
</div>

<br>

<h2>🎯 주요 타겟층</h2>
<div>
  <b>소비자</b>
  <ul>
    <li>원하는 취향의 향수를 온라인으로 구매하는데 어려움을 느끼는 소비자</li>
    <li>향수 상세 페이지를 하나 하나 확인하기 번거롭고 향에 무지한 소비자</li>
    <li>좀 더 직관적인 향수 경험을 얻고 싶은 소비자</li>
  </ul>
  <b>판매자</b>
  <ul>
    <li>판매하는 상품의 이미지를 간편하게 전달하고 싶은 판매자</li>
    <li>판매하는 상품의 향을 시각적으로 홍보하고 싶은 판매자</li>
  </ul>
</div>

<br>

## 🧩 주요 기능
### 1. 생성형 AI 기반 향수 배경 이미지 생성 서비스: 🎯 판매자 타겟

<p align="center">
<img width="454" height="448" alt="스크린샷 2025-12-02 오후 4 11 31" src="https://github.com/user-attachments/assets/01946a66-6336-4e53-afae-7af1df38260c" />
</p>


**(1) 배경 제거**
<p></p>

판매자로부터 받은 향수 병 이미지의 배경을 [**rembg**](https://github.com/danielgatis/rembg) 라이브러리를 사용하여 제거
<p></p>

**(2) 배경 이미지 생성**
<p></p>

사용자로부터 입력받은 향수의 재료와 무드 정보를 기반으로 [**Stable Diffusion 3.5 large**](https://huggingface.co/stabilityai/stable-diffusion-3.5-large) 모델을 활용해 어울리는 배경 이미지 생성
<p></p>

- **이미지 생성 최적화 전략**
<p></p>

**하이퍼파라미터 튜닝**과 **googletrans** 기반 번역 파이프라인을 활용한 **프롬프트 엔지니어링**을 통해, 원하는 구도의 이미지를 안정적으로 생성할 수 있도록 구현
<p></p>

**(3) 이미지 합성**
<p></p>

**pillow** 라이브러리를 이용해 배경이 제거된 향수 제품 이미지와 생성된 배경 이미지를 자연스럽게 합성
<p></p>

<br>

### 2. LLM을 활용한 챗봇 제품 검색/추천 기능: 🎯 소비자 

<p align="center">
<img width="454" height="448" alt="스크린샷 2025-12-02 오후 4 11 40" src="https://github.com/user-attachments/assets/184b6a2a-b8b5-4fea-b802-3f7f1fe0cf81" />
</p>

**(1) 검색 증강 생성(RAG)**
<p></p>
약 1,500개의 향수 제품 데이터를 크롤링하여 벡터화하고, 이를 기반으로 RAG 구조를 통해 LLM에 제공
<p></p>

**(2) 시스템 프롬프팅**
<p></p>
향수 쇼핑을 웹사이트 기준에 맞춰, 사용자에게 적합한 답변을 제공하도록 시스템 프롬프트 설정
<p></p>

**(3) OpenAI LLM API 연동**
<p></p>
GPT-4o-mini API를 활용하여 자연스럽고 편안한 대화형 챗봇 서비스를 제공. RAG에서 관련 정보를 찾지 못했다면 GPT 자체 기반 지식을 이용하도록 구현
<p></p>

**(4) LangChain 라이브러리 연동**
<p></p>
LangChain을 활용해 대화 히스토리를 기억하고, RAG 방식으로 검색된 문서와 질문을 결합한 프롬프트를 자동 생성. 검색 기반 정보(RAG)와 LLM API를 유기적으로 연결하여 검색 정보와 대화 맥락을 반영한 고품질 응답 생성
<p></p>
