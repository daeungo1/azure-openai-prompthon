---
title: 'Lab 01: LLM과 Azure AI 서비스 소개'
layout: default
nav_order: 1
---
#### LLM과 Azure AI 서비스 소개

이 실습에서는 Azure AI를 사용하여 대용량 언어 모델과 작업하는 방법에 대해 알아보겠습니다.

주로 생성 프로세스에 대한 개요에 초점을 맞추고, 다음 단계에서는 빌드, 평가, 배포 및 모니터링 프로세스에 대해 자세히 알아보겠습니다.

#### 사전 요구 사항

Azure 구독이 필요하며, AI 프로젝트와 AI 허브 리소스, 콘텐츠 안전 서비스, AI 검색 서비스를 생성할 수 있는 환경이 필요합니다.

#### 설정

- [AI 프로젝트 및 AI 허브 리소스 생성](#ai-프로젝트-및-ai-허브-리소스-생성)
- [Azure OpenAI 모델 배포](#azure-openai-모델-배포)

#### 실습 단계
- AI Studio에서 Project 생성하기
- AzureAI Studio Playground 사용하기.

  

#### 설정

#####  AI 프로젝트 및 AI 허브 리소스 생성

먼저 Azure AI Studio에서 허브 및 프로젝트를 생성하여 시작할 수 있습니다. (실습에서는 미리 생성 완료)

브라우저에서 다음 주소를 입력하고 엔터 키를 눌러 이동합니다: https://ai.azure.com

Azure 계정으로 로그인한 후 다음 화면이 표시됩니다:

![LLMOps Workshop](images/16.12.2023_13.35.18_REC.png)

**빌드** 탭에서 **새 허브**를 선택하여 생성합니다.
AI Studio 첫 화면에서 연결 리소스 선택
<img width="976" alt="image" src="https://github.com/user-attachments/assets/6463080e-f7cb-422f-bad8-8a6faa8c303a">
생성하기
<img width="755" alt="image" src="https://github.com/user-attachments/assets/5de7ddfc-0e18-49d8-9059-4f8333474552">


프로젝트를 생성하기 위해 허브에 들어간 후 **프로젝트 생성**을 선택합니다.
<img width="979" alt="image" src="https://github.com/user-attachments/assets/aa788897-9256-4bbe-bd9a-4d0ac2f77ca7">

- 허브의 리소스를 프로젝트간 공유를 할 수 있습니다.


##### Azure OpenAI 모델 배포

AI 프로젝트를 생성한 후에는 OpenAI 모델을 배포하여 응용 프로그램에서 사용할 프롬프트를 실험할 수 있습니다.

AI Studio의 **빌드** 탭에서 새로 생성한 프로젝트에 액세스한 다음 **배포** 옵션을 선택하고 **생성 (실시간 엔드포인트)**를 클릭합니다.

![LLMOps Workshop](images/06.02.2024_21.44.42_REC.png)

모델 목록에서 **gpt-4**를 선택합니다.

![LLMOps Workshop](images/12.03.2024_16.22.33_REC.png)

다음 화면에서 배포의 이름을 정의하고, 버전 필드에서 최신 버전을 선택합니다. 아래 예시에서는 버전 **0125-Preview** (gpt4-turbo)를 선택했습니다.

![LLMOps Workshop](images/12.03.2024_16.31.47_REC.png)

> **고급 옵션**을 클릭하고 최소 40K **분당 토큰 제한**을 선택하여 다음 단계에서 원활한 실행을 보장합니다.

이제 **배포**를 클릭하면 모델 배포가 생성됩니다. 이제 Playground에서 테스트할 수 있습니다.

 


#### 실습 단계

##### 1) AzureAI Studio Playground 사용하기

배포 정보가 표시된 화면에서 **Playground에서 열기** 버튼을 선택합니다.

![LLMOps Workshop](images/16.12.2023_16.29.30_REC.png)

###### 시스템 메시지(한국어 버전) :
당신은 고객과 통신사 대표 간의 대화에서 가치 있는 정보를 추출하여 각 대화 전사에 대한 JSON 파일을 생성하는 AI 어시스턴트입니다. 다음과 같은 형식으로 JSON으로 추출하고 포맷팅합니다:
1. 고객 이름 [name]
2. 고객 연락처 전화번호 [phone]
3. 대화의 주요 주제 [topic]
4. 고객 감정 (중립, 긍정, 부정) [sentiment]
5. 대화에서 대리인이 처리한 방식 [agent_behavior]
6. 대화의 최종 결과 [outcome]
7. 대화의 간단한 요약 [summary]

확실한 정보만 추출하세요. 확실하지 않은 경우 JSON 파일에 "Unknown/Not Found"라고 작성하세요.

###### 시스템 메시지(영문 버전) :
 You're an AI assistant that helps Lamna Healthcare Customer Service to extract valuable information from their conversations by creating JSON files for each conversation transcription you receive. You always try to extract and format as a JSON:
 1. Customer Name [name]
 2. Customer Contact Phone [phone]
 3. Main Topic of the Conversation [topic]
 4. Customer Sentiment (Neutral, Positive, Negative)[sentiment]
 5. How the Agent Handled the Conversation [agent_behavior]
 6. What was the FINAL Outcome of the Conversation [outcome]
 7. A really brief Summary of the Conversation [summary]

 Only extract information that you're sure. If you're unsure, write "Unknown/Not Found" in the JSON file.

위를 복사한 후 **변경 사항 적용**을 선택하세요.


![LLMOps Workshop](images/06.02.2024_21.48.36_REC.png)

그런 다음 다음 텍스트를 채팅 세션에 입력하고 전송 버튼을 클릭하세요:

한글 버전 :
```
Agent: 안녕하세요, 텔코 고객 서비스에 오신 것을 환영합니다. 저는 홍길동입니다. 어떻게 도와드릴까요?
Client: 안녕하세요, 홍길동씨. 저는 모바일 데이터 요금제에 문제가 있어 전화드렸습니다. 인터넷이 매우 느리고 앱을 사용하거나 인터넷을 브라우징할 수 없습니다.
Agent: 불편을 드려서 정말 죄송합니다, 귀하의 전화번호와 성함을 알려주시겠어요?
Client: 네, 좋아요. 제 번호는 011-4567-8910이고 제 이름은 홍길동입니다.
Agent: 감사합니다, 홍길동씨. 귀하의 요금제와 데이터 사용량을 확인해 보겠습니다. 잠시만 기다려주세요.
Client: 네, 감사합니다.
Agent: 홍길동씨, 귀하의 요금제를 검토했고 월 2GB의 기본 요금제를 가입하셨다고 보입니다. 맞나요?
Client: 네, 맞습니다.
Agent: 그렇다면 귀하의 데이터 한도의 90%를 사용하셨으며, 이번 달 말까지 200MB만 사용 가능합니다. 그래서 브라우징 속도가 낮아진 것입니다.
Client: 뭐라고요? 어떻게 그럴 수 있죠? 저는 핸드폰에서 인터넷을 거의 사용하지 않아요. 이메일이나 소셜 네트워크를 가끔 확인할 뿐이에요. 동영상을 보거나 큰 파일을 다운로드하지 않아요.
Agent: 이해합니다, 홍길동씨. 하지만 앱의 자동 업데이트, 백업, GPS 등 일부 애플리케이션은 귀하가 인식하지 못하고 배경에서 데이터를 소비합니다.
Client: 그래도 제가 요금제를 가입할 때 그런 설명을 받지 못했어요. 2GB로 한 달 동안 충분하다고 말했는데요. 속은 것 같아요.
Agent: 죄송합니다, 홍길동씨. 우리의 의도는 귀하를 속이는 것이 아니었습니다. 해결책을 제안해 드리겠습니다: 원하신다면 더 많은 데이터 용량과 더 빠른 속도를 제공하는 더 높은 요금제로 변경하실 수 있습니다. 이렇게 하면 더 나은 브라우징 경험을 즐길 수 있습니다.
Client: 그렇다면 얼마나 비용이 드나요?
Agent: 특별한 할인을 제공해 드립니다. 월 10페소 추가로 지불하시면 5GB 데이터와 4G 속도를 제공하는 프리미엄 요금제를 이용하실 수 있습니다. 관심이 있으신가요?
Client: 음, 잘 모르겠어요. 다른 옵션이 없을까요? 더 많은 속도를 추가 비용 없이 제공할 수는 없을까요?
Agent: 죄송합니다, 홍길동씨. 우리가 제공할 수 있는 유일한 옵션입니다. 요금제를 변경하지 않으시면 정상 속도를 되찾기 위해 다음 달까지 기다려야 합니다. 또는 추가 데이터 패키지를 구매할 수도 있지만, 요금제 변경보다 비용이 더 많이 들 수 있습니다.
Client: 그럼 생각해 볼게요. 나중에 전화해서 확인해도 될까요?
Agent: 물론, 홍길동씨. 언제든지 전화해 주세요. 지금 전화한 번호와 동일한 번호입니다. 도움이 필요한 게 더 있으신가요?
Client: 아니요, 그게 다예요. 신경 써 주셔서 감사합니다.
Agent: 홍길동씨, 감사합니다. 좋은 하루 보내세요. 안녕히 가세요.
```
영문 버전 : 
```
Agent: Hello, welcome to Lamna Healthcare customer service. My name is Juan, how can I assist you?
Client: Hello, Juan. I'm calling because I'm having issues with my medical bill I just received few days ago. It's incorrect and it does not match the numbers I was presented before my medical procedure.
Agent: I'm very sorry for the inconvenience, sir. Could you please tell me your phone number and your full name?
Client: Yes, sure. My number is 011-4567-8910 and my name is Martín Pérez.
Agent: Thank you, Mr. Pérez. I'm going to check your plan, you deduction limits and current year transactions towards your deductions. One moment, please.
Client: Okay, thank you.
Agent: Mr. Pérez, I've reviewed your plan and I see that you have the Silver basic plan of $3,000 deductable. Is that correct?
Client: Yes, that's correct.
Agent: Well, I would like to inform you that you have not met your deductible yet and $2,800 of the procedure will be still be your responsability and that will meet your deductible for the year.
Client: What? How is that possible? I paid over $2,000 already towards my deductable this year, I should only be $1,000 away from reaching my deductible not $2,800. 
Agent: I understand, Mr. Pérez. But keep in mind that not all fees your pay to doctors and labs and medications count towards your deductible. 
Client: Well, but they didn't explain that to me when I contracted the plan. They told me that everything I pay from my pocket towards doctors, specialists, labs and medications will count towards my deductable. I feel cheated.
Agent: I apologize, Mr. Pérez. It was not our intention to deceive you. If you think the deductable is too high, I recommed changing the plan to Gold at the next renewal window and that will bring the deductable to $1,000 for the new year.
Client: And how much would that cost me?
Agent: The plan rates will come out in November, you can call us back then or check the new rates online at that time.
Client: Mmm, I don't know. Isn't there another option? Can't you reduce the amount I have to pay for this bill as I was not explained how the deductible work correctly?
Agent: I'm sorry, Mr. Pérez. I don't have the power to change the bill or your deductible under the current Silver plan.
Client: Well, let me think about it. Can I call later to confirm?
Agent: Of course, Mr. Pérez. You can call whenever you want. The number is the same one you dialed now. Is there anything else I can help you with?
Client: No, that's all. Thank you for your attention.
Agent: Thank you, Mr. Pérez. Have a good day. Goodbye.
```

결과:

![LLMOps Workshop](images/17.12.2023_20.36.17_REC.png)
 

