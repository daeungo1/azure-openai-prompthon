
## Azure AI Search에서 직접 Index 생성하기

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
 
.

##### 2.2 Overview 탭에서 Import data 선택
<img width="452" alt="image" src="https://github.com/user-attachments/assets/01885fc5-268d-4b5d-b067-c1fdfd77a35f">
- 대상 Blob Storage의 Container 선택 : wikidata
<img width="608" alt="image" src="https://github.com/user-attachments/assets/e278142d-7a92-4535-a489-80dbbb39505c">

- 데이터명  wikidata, Parsing mode는 JSON lines로 설정 후, Choose an existing connection 클릭
  <img width="611" alt="image" src="https://github.com/user-attachments/assets/dd2297d3-c123-4cde-af0d-b5ca4f9854ab">
- 대상 Storage Account 선택 및 container 선택
  <img width="971" alt="image" src="https://github.com/user-attachments/assets/548913e1-246d-4312-a97a-60d98bfd9708">
  <img width="848" alt="image" src="https://github.com/user-attachments/assets/310c514d-2897-4e6f-aba2-57f401293dea">
- 다음 단계 진행 후, Customize target index 진행
  <img width="251" alt="image" src="https://github.com/user-attachments/assets/d0fb86cf-e83f-4741-b964-d8adb1949692">
- index 이름 설정 및 key는 id로 지정하기
  <img width="785" alt="image" src="https://github.com/user-attachments/assets/2ea3eb6d-0691-4d07-8f32-cb6ee0931b8c">

- AzureSearch_DocumentKey 이하 필드는 delete하기
  <img width="1045" alt="image" src="https://github.com/user-attachments/assets/508bfe3f-a45e-4efb-94df-0a8e2735a9c4">

- content_vector 필드의 Type 을 Collection(Edm.Single)로 변경하기
  <img width="373" alt="image" src="https://github.com/user-attachments/assets/6a0d602b-ea52-45ae-b05e-dea0e14c0b15">
- content_vector 필드에 대하여  configure vector field 클릭
  <img width="920" alt="image" src="https://github.com/user-attachments/assets/8c2f68f0-47e3-440b-9a6f-0cc28879922d">

- Dimensions를 embedding-ada-002의 vector size이 1536으로 설정후 Vector Search Profile 생성하기 클릭
  <img width="905" alt="image" src="https://github.com/user-attachments/assets/351381fe-e0de-40d8-a7c3-f4b7ce4e1c8d">
- Algorithms 생성하기 클릭
  <img width="472" alt="image" src="https://github.com/user-attachments/assets/deae83b5-98d7-46fd-a65c-4a3082c72dad">

- hnsw 또는 KNN 선택 후, 저장 두번 클릭
  <img width="479" alt="image" src="https://github.com/user-attachments/assets/d14a1bd8-38c0-4a6f-ab7e-3466fbf7771c">
  <img width="485" alt="image" src="https://github.com/user-attachments/assets/0fc93f8a-f88a-4c3b-8205-c0d6f33ce98e">

- Next : Create an Indexer 클릭 후, Submit
  <img width="661" alt="image" src="https://github.com/user-attachments/assets/aa52a316-19b5-43a9-a643-7b6ea634fff8">
- Indexes에서 해당 Index 선택 및 검색 버튼 클릭
  <img width="904" alt="image" src="https://github.com/user-attachments/assets/12826e90-00a5-454a-8664-a3f8fb4d7e18">
  <img width="869" alt="image" src="https://github.com/user-attachments/assets/9a845f5d-820b-4011-a374-44d890d50f6c">

- Semantic Configurations 생성하기
  <img width="602" alt="image" src="https://github.com/user-attachments/assets/bf009a00-fbab-4616-9244-47ae69623d7e">
  Name은 semantic으로 설정후, title field와 field name에 설정 후 저장
  <img width="520" alt="image" src="https://github.com/user-attachments/assets/bf9eb1a3-9c44-4886-8ed0-3483bdcb982d">
- 최종 저장 버튼 클릭
  <img width="887" alt="image" src="https://github.com/user-attachments/assets/142783e2-03ed-4b46-b897-800843e57e32">




  

   
