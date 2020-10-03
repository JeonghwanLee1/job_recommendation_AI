# :bulb: job_recommendation AI model
채용공고를 보고 개발자의 지원 유무를 파악하는 AI 추천모델(Graph, Decision Tree, Random Forest)

## :floppy_disk: 데이터셋
job_companies.csv : company 별 job과 규모    
<img src="https://user-images.githubusercontent.com/43736669/94919776-fcce3780-04ef-11eb-8217-5b24a8303fef.png">  
job_tags.csv : job 별 tag  (job에 대응되는 기술)  
<img src="https://user-images.githubusercontent.com/43736669/94920971-4f105800-04f2-11eb-8041-37ad4d791527.png">  
tags.csv : tag 별 기술 이름 (기술 태그 Hash에 대응되는 이름)  
<img src ="https://user-images.githubusercontent.com/43736669/94921035-6e0eea00-04f2-11eb-9d67-c31336c783f2.png">  
user_tags.csv : user 별 관심 기술 목록  
<img src ="https://user-images.githubusercontent.com/43736669/94921123-9860a780-04f2-11eb-8d6c-5f192d35c645.png">  
train.csv(train set) : user가 해당 job에 지원하였는지 여부  
<img src ="https://user-images.githubusercontent.com/43736669/94921312-086f2d80-04f3-11eb-8256-c0e9c5cab12a.png">  

## :thought_balloon:파생 데이터
1) 회사의 규모 
미기입 : none  
10명 이하 : small   
10명 이상 100명 이하 : medium   
100명 이상 : big  
job_company로부터 추출  
 
2) weighted graph
개발자가 등록하지 않았지만 현재 기술스택과 관련도가 높은 기술을 구하기 위해 각 기술마다 다른 기술과의 연관도를 저장한 weighted graph.  
user_tag로부터 추출  
  
3) minorstacks   
내가 보유한 기술과 연관이 높은 기술 top 10. 위의 weighted graph로부터 도출  
  
4) 일치 majorstacks  
회사에서 요구한 기술과 내가 보유한 기술의 일치 수  
  
5) 일치 minorstacks  
회사에서 요구한 기술과 내가 보유한 minorstacks의 일치 수   

6) majorstacks/companystacks, minorstacks/ companystacks   
majorstack,minorstack 일치 수 / 회사에서 요구한 기술의 수   
  
7) majorstacks/mystacks   
majorstack 일치 수 / 내가 등록한 기술 수  

## :computer: 사용 모델    
1) decision tree(sklearn)   
회사의 규모, 기술 일치율, 기술 일치수, 관련기술 일치율, 관련기술 일치수, 기술 일치율(내 기술수 기준), 내 기술수 이상 7개 column 기준으로 decision Tree 제작  
<img src = "https://user-images.githubusercontent.com/43736669/94986971-fb5b4880-059d-11eb-92a7-a10b3e890f57.png">  
  
2) randomforest    
  
## :chart_with_downwards_trend: 결과  
<img src="https://user-images.githubusercontent.com/43736669/94987189-46c22680-059f-11eb-990e-bc406bd18326.png">  
programmers 과제란 채점 기준   
Decision Tree : 78.64%  
Random Forsest : 78.43%  
  
## :computer: 기술 스택  
python,jupyter notebook, numpy, pandas, sklearn, pydotplus  
