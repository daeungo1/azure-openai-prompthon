# GPT 기초, 사용 사례 및 샘플 솔루션 - 한국어 버전
이 리포지토리에는 Azure OpenAI에서 제공하는 GPT(Generative Pre-trained Transformer)를 사용하는 기본 방법을 이해하고 샘플 솔루션을 및 다양한 사용 사례를 통해 이해에 도움이 되는 리소스가 포함되어 있습니다.

- PDF자료 : [2024_KT_AOAI_Prompthon.pdf](https://github.com/user-attachments/files/16061561/2024_KT_AOAI_Prompthon.pdf)

- Github 링크 : bit.ly/4bHljhT

![bit ly_4bHljhT](https://github.com/daeungo1/azure-openai-prompthon/assets/122502313/f891824e-28b9-4a48-bfa7-88c863eb4316)

## 시작하기
Codespace 환경을 통해서 개발 환경을 빠르게 시작할 수 있습니다.  
**아래 버튼을 클릭**하여 GitHub Codespaces에서 저장소를 열어서 시작하세요!  

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/daeungo1/azure-openai-prompthon?quickstart=1)

Python 실행을 위한 Runtime 환경은 `python=3.11.4` 추천합니다. 위 버튼을 누르고 약 7분이 경과되면, .devcontainer에 정의된 개발 환경 및 라이브러리 설치가 완료되며, 브라우저에 Visual Studio Code IDE가 표시됩니다.  

### 실습에 사용하는 GPT 버전
gpt-4o 모델 또는 gpt-4-turbo 최신 모델을 활용하는 것을 추천 드립니다. (2024-06-25 기준)

### 설정하기
>안전한 로컬 환경에서의 키관리를 위해 실습에 필요한 API Endpoint 또는 API Key는 ***.env*** 파일을 활용하는 것을 강력히 추천합니다. 예를 들어 [.env.sample](./.env.sample) 파일을 복사하여 `.env` 파일을 만들고 해당 API KEY 정보를 입력하여 사용합니다.

### 개발환경 정보
>**Python 버전은 3.11.4, Azure OpenAI 버전은 1.13.3에서 실행할 수 있습니다. - 2024-03-17**  
해당 컨텐츠는 DevContainer 기반으로 개발에 필요한 환경설정이 정의되어져 있습니다. GitHub Codespace를 활용하거나, 로컬에 Docker를 설치한 상태에서 Visual Stduio Code IDE에 해당 Repository를 다운로드 받을 경우, 자동으로 컨테이너에 개발환경(Python Runtime 3.11.4, Azure OpenAI 1.13.3)을 설치합니다. .env 파일에 필수 API 정보를 입력하고 저장후 사용하세요.  
----  
 
## GPT란?
GPT(Generative Pre-trained Transformer)는 OpenAI에서 개발한 LLM(Large Language Model)입니다. 트랜스포머 아키텍처 기반의 딥러닝 모델입니다. 자세한 내용은 [OpenAI](https://openai.com)를 참조하세요. 
 
## 개발환경 선택하기
>해당 실습을 원활하게 제공하기 위해서 .devcontainer 환경을 제공하고 있습니다. 나의 PC에 Docker나 IDE 설치를 원하지 않는다면, `Codespace`를 권장합니다. 
- Local PC에 `Docker`가 설치되어 있다면, VS Code에서 Reopen DevContainer를 실행하여 Docker에 컨테이너 이미지를 생성하면 자동으로 실습 가능한 런타임과 패키지들이 설치되도록 구성되어 있습니다.
- GitHub에서 제공하는 `Codespace`를 활용하면, Codespace가 제공하는 리모트 VM에 컨테이너가 올라가고, Codespace가 제공하는 웹브라우저 용 VS Code를 통해 즉시 개발을 진행할 수 있습니다.

참고: `Codespace`는 GitHub 개인 계정에게 월 15GB의 저장공간과 120 시간/core의 VM을 무료로 제공합니다. [자세한 가격 정보 참고는 클릭](https://docs.github.com/en/billing/managing-billing-for-github-codespaces/about-billing-for-github-codespaces)

## 프로그램 자료
이 Repository는 https://github.com/Azure/azure-openai-samples 을 기반으로 만들었습니다.  


## 참고 고객 사례
`Gen AI Workshop & Hackathon` 을 진행한 고객 중 공개된 회사에 대해서만 아래에 관련 정보를 기록합니다.  
- 2023-07: **우아한형제들** - [우아한형제들, 사내 해커톤 ‘우아톤 2023’ 진행](https://zdnet.co.kr/view/?no=20230717092217)  
- 2024-01: **Finda** - [핀다, 한국MS와 사내 해커톤 '2024핀다톤' 개최](https://www.etnews.com/20240205000064)

## Contributing
We welcome contributions to this repository. If you have any ideas or suggestions, please feel free to open an issue or submit a pull request.

As technologies changes very fast, we endevour to keep this repository updated as quick as possible. However, this is heavily rely on keen community contributors to make this happen.
