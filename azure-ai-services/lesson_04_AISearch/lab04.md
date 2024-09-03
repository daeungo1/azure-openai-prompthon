<img width="773" alt="image" src="https://github.com/user-attachments/assets/d397c26e-7add-4d48-8974-2677687083af">## Azure AI Search에서 직접 Index 생성하기

1. Azure Storage Account 에서 Container 생성하기 : pdfdata / wikidata
   <img width="1110" alt="image" src="https://github.com/user-attachments/assets/f1ca4842-8692-4e13-a52d-cff5b95392f3">
   데이터는 업로드하기 :
   - sample데이터 employee_handbook.pdf 를 pdfdata container에 업로드
   - wiki json line 파일 wiki_data_embeddings을 wikidata container에 업로드
   <img width="1093" alt="image" src="https://github.com/user-attachments/assets/37403654-e3fd-4891-8153-4f60c09f5c7d">
   <img width="830" alt="image" src="https://github.com/user-attachments/assets/86e46c3d-febb-4bc3-a182-b96f80cf714d">
   -
   <img width="1103" alt="image" src="https://github.com/user-attachments/assets/3e11f8cb-0c8b-44b1-8ef9-4c5ab407d75e">
   <img width="766" alt="image" src="https://github.com/user-attachments/assets/318541c0-a960-41e5-9610-5ce0390f0722">
.




2. AI search에서 데이터 로드 및 검색 Index 생성하기
##### 2.1 Overview 탭에서 Import and Vetorize data 선택
<img width="764" alt="image" src="https://github.com/user-attachments/assets/13f051d4-e37e-4bf3-b92b-66e2d9c2d686">
- Blob storage 선택 후, 대상 Storage Account 및 Container pdfdata 선택
<img width="866" alt="image" src="https://github.com/user-attachments/assets/00307227-1d9b-4247-b551-717bfd741ef5">
<img width="833" alt="image" src="https://github.com/user-attachments/assets/ed6c6d41-70de-4061-8e0a-91bf4fbc6c3d">
- Vectorize your text 를 위한 OpenAI 서비스 및 Embedding 모델 선택
<img width="919" alt="image" src="https://github.com/user-attachments/assets/6c59adb2-e255-46f7-8786-35d421cec179">

<img width="785" alt="image" src="https://github.com/user-attachments/assets/9c0e421a-9660-4331-9658-b9c785040c69">

- Index 이름 설정 및 생성하기
  <img width="773" alt="image" src="https://github.com/user-attachments/assets/9be65933-6685-4746-bc7d-aa8a8bb6b2eb">

- Indexes에서 해당 Index 선택 및 검색 버튼 클릭
  <img width="853" alt="image" src="https://github.com/user-attachments/assets/d3a3daea-9417-44f8-af1f-cc48e57c58e6">
  <img width="944" alt="image" src="https://github.com/user-attachments/assets/eb35456e-fa31-4a06-a5e1-78886636aeec">


   
