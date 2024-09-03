---
title: 'Lab 03: LLM 평가 및 배포'
layout: default
nav_order: 4
---
#### LLM 평가 및 배포

#### 사전 요구 사항

AI 허브 리소스와 AI 검색 서비스를 생성할 수 있는 Azure 구독이 필요합니다.

#### 설정

이 랩을 수행하기 전에 1번 레슨 이후에 실행 중인 경우 이 단계에 대해 걱정할 필요가 없습니다. 그렇지 않은 경우 **1번 레슨**의 **설정**을 따라 Azure AI Studio에서 프로젝트와 관련 리소스를 생성하고 GPT-4 모델을 배포하세요.

#### 랩 단계

이 랩에서 다음 단계를 실행합니다:

1) 채팅 플로우 평가하기.

2) RAG 플로우를 온라인 관리 엔드포인트에 배포하기.

##### 1) 채팅 플로우 평가하기

브라우저에서 https://ai.azure.com을 입력하세요.

이전에 생성한 프로젝트를 선택하고 **Build** 탭의 **Tools** 섹션에서 **Prompt flow** 항목을 선택하세요.

###### 1.1) 채팅 플로우 평가를 위해 준비하기

이전에 생성한 RAG 플로우를 평가하려면 이 플로우의 출력 노드에 추가 정보를 포함해야 합니다. 특히, 답변을 생성하는 데 사용된 컨텍스트를 포함해야 합니다.

이 정보는 평가 플로우에서 사용됩니다. 이를 위해 다음 단계를 따르세요:

**Prompt Flow**의 Flows 섹션에서 이전 랩에서 생성한 `Multi-Round Q&A on Your Data` 플로우를 엽니다. 이것이 우리가 평가에 사용할 플로우입니다.

![LLMOps Workshop](images/26.02.2024_23.43.08_REC.png)

Outputs 노드에서 `documents`라는 새로운 출력을 생성하세요. 이 출력은 `lookup` 노드에서 검색된 문서를 포맷팅한 `generate_prompt_context` 노드에서 생성된 문서를 나타냅니다.

`generate_prompt_context` 노드의 출력을 `documents` 출력에 할당하세요. 아래 이미지와 같이 설정하세요.

![LLMOps Workshop](images/07.02.2024_23.37.47_REC.png)

다음 섹션으로 이동하기 전에 **Save**를 클릭하세요.

###### 1.2) 평가 플로우 생성하기

**Build** 탭의 **Tools** 섹션에서 **Prompt flow** 항목에서 파란색 **Create** 버튼을 클릭하세요.

![LLMOps Workshop](images/05.01.2024_00.43.51_REC.png)

**Evaluation Flow** 필터를 선택하고 **QnA Groundedness Evaluation** 카드의 **Clone**을 클릭하세요.

![LLMOps Workshop](images/26.02.2024_23.14.59_REC.png)

플로우를 복사하기 위해 다른 **Clone** 버튼을 클릭하세요.

![LLMOps Workshop](images/26.02.2024_23.18.12_REC.png)

다음 구조를 가진 플로우가 생성됩니다:

![LLMOps Workshop](images/26.02.2024_23.21.02_REC.png)

`groundedness_score` 노드의 `Connection` 필드를 gpt-4 배포를 가리키도록 업데이트하고 max_tokens를 `1000`으로 업데이트하세요. 다음 그림과 같이 설정하세요.

![LLMOps Workshop](images/26.02.2024_23.24.46_REC.png)

연결 정보를 업데이트한 후, 평가 플로우에서 **Save**를 클릭하고 **Prompt Flow** 항목의 Flows 섹션으로 이동하세요.

이제 이전에 설명한 **1.2 섹션**에서 **두 개**의 추가 평가 플로우, `QnA Relevance Evaluation`와 `QnA GPT Similarity Evaluation`를 생성하기 위해 동일한 단계를 반복하세요. 아래 두 이미지는 이러한 플로우가 prompt flow 갤러리에서 어디에 있는지 보여줍니다.

> 두 개의 추가 평가 플로우를 생성해야 하므로 **1.2 섹션** 단계를 두 번 반복합니다.

> 각 플로우에 대해 Azure OpenAI 연결을 설정할 LLM 노드의 이름이 약간 다르다는 점에 유의하세요: 각각 **relevance_score**와 **similarity_score**입니다.

QnA Relevance Evaluation:

![LLMOps Workshop](images/14.03.2024_16.04.30_REC.png)


QnA GPT Similarity Evaluation:

![LLMOps Workshop](images/14.03.2024_16.05.01_REC.png)


###### 1.3) 평가 실행하기

**Prompt Flow**의 Flows 섹션에서 이전 랩에서 생성한 `Multi-Round Q&A on Your Data` 플로우를 엽니다. 이것이 우리가 평가에 사용할 플로우입니다.

**Runtime** 드롭다운에서 **Start**를 선택하여 자동 실행을 시작하세요. 이러한 런타임은 플로우 작업에 유용합니다.

![LLMOps Workshop](images/13.03.2024_10.31.21_REC.png)

이제 **Evaluate** 메뉴에서 **Custom evaluation** 옵션을 선택하세요.

![LLMOps Workshop](images/05.01.2024_01.31.10_REC.png)

`Prompt_variants` 옵션에서 **two variants**만 실행하도록 선택하여 GPT-4 모델 할당량을 초과하지 않도록 주의하세요. 다음 예시 이미지와 같이 설정하세요.

![LLMOps Workshop](images/15.03.2024_00.36.03_REC.png)

**Add new data**를 선택하세요.

![LLMOps Workshop](images/26.02.2024_23.51.33_REC.png)

lesson_03 폴더 내의 data.csv 파일을 업로드하세요.

![LLMOps Workshop](images/26.02.2024_23.54.35_REC.png)

**Add**를 클릭한 후, 아래 이미지와 같이 입력 필드를 매핑하세요.

![LLMOps Workshop](images/05.01.2024_01.36.19_REC.png)

방금 생성한 세 개의 평가 플로우를 선택하세요.

![LLMOps Workshop](images/14.03.2024_22.29.58_REC.png)

지금까지 잘 하셨습니다! 이제 다음 단계로 넘어갑시다. **Next**를 클릭하여 각 평가 플로우에 대해 `question`, `context`, `ground_truth`, `answer` 필드를 설정하세요. 이를 위한 세 가지 이미지에서 어떻게 수행하는지 확인할 수 있습니다.

> **참고:** 올바른 값을 선택했는지 확인하기 위해 잠시 시간을 내어주세요. 정확한 지표 계산에 중요합니다. 마법사에서 처음에 제시된 기본값은 다음 이미지에서 나타난 값과 동일하지 않습니다. 좋은 작업을 계속하세요!

**QnA GPT Similarity Evaluation**

![LLMOps Workshop](images/14.03.2024_23.08.34_REC.png)

**QnA Groundedness Evaluation**

![LLMOps Workshop](images/14.03.2024_23.11.52_REC.png)

**QnA Relevance Evaluation**

![LLMOps Workshop](images/14.03.2024_23.12.25_REC.png)

평가를 시작하려면 **Submit**을 클릭하세요.

![LLMOps Workshop](images/05.01.2024_01.44.01_REC.png)

평가 프로세스가 시작되었습니다. **Build** 탭 아래의 **Evaluation** 섹션으로 이동하여 모든 평가(각 변형별 하나씩)을 확인할 수 있습니다.

![LLMOps Workshop](images/15.03.2024_00.52.20_REC.png)

특정 평가 결과를 선택하면 해당 결과의 상세 정보를 확인할 수 있습니다.

또한 **Switch to dashboard view**를 선택하여 다른 변형의 라운드 간의 테이블 및 시각적 비교를 제공하는 대시보드에 액세스할 수 있습니다. 다음 이미지에서 확인할 수 있습니다.

*테이블 비교*

![LLMOps Workshop](images/15.03.2024_01.28.00_REC.png)

*차트 비교*

![LLMOps Workshop](images/15.03.2024_01.21.34_REC.png)

##### 2) RAG 플로우를 온라인 관리 엔드포인트에 배포하기

이전 랩에서 생성한 **Multi-Round Q&A on Your Data** 플로우를 엽니다.

플로우를 열고 다음 링크에서 지시사항을 따르세요:

https://learn.microsoft.com/en-us/azure/ai-studio/how-to/flow-deploy