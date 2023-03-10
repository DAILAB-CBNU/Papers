#### 논문 - Perceived or Not Perceived: Film Character Models for Expressive NLG
 
- 저자: Marilyn A. Walker, Ricky Grant, Jennifer Sawyer, Grace I. Lin, Noah Wardrip-Fruin, and Michael Buell
- ACM 2011
- [논문 링크](https://users.soe.ucsc.edu/~maw/papers/icids-v12.pdf)
-----------------
- **목적**
  - 대화형 대화 작성에 대한 개인 실무자의 전문 지식에 의존하고 있으며, 종종 여러 번 다시 작성됨
    - 사용자의 선택과 이력에 따라 스토리가 달라질 수 있어, 사용자가 여러 번 경험하고자 하는 스토리를 제작할 때 문제가 생김
    -  이야기 대화를 위한 언어 생성에 대한 연구는 거의 이루어지지 않았음
  - 이 논문은 영화 스크린 플레이의 IMSDb 말뭉치에 대해 훈련된 말뭉치 기반 통계 표현 언어 생성 엔진을 기반으로 "캐릭터 음성"을 자동으로 생성하는 접근 방식을 테스트 
  - 본 논문에서는 영화 대사 말뭉치를 활용하여 캐릭터 언어 스타일 모델을 학습하는 방법을 제시
    - (1) 예시 : 캐릭터 언어 스타일의 학습 모델, 예를 들어 쿠엔틴 타란티노의 영화 펄프 픽션의 대화 모델(그림 1)    
      ![image](https://user-images.githubusercontent.com/49019292/223053333-1f4a5a26-cd95-4723-9b5f-9e4ea8b88bce.png)      
    - (2) 표현 언어 생성 엔진인 PERSONAGE의 매개 변수를 제어하기 위해 학습된 모델을 사용
    - (3) 이러한 모델을 사용하여 만들어진 캐릭터 발화에 대한 인간의 인식에 대한 실험
  - 게임 SpyFeet을 플레이하는 프로토타입 역할의 맥락에서 우리의 접근 방식을 테스트
-------------------------------------------------------------
- **방법**
  - Learning Character Models
    - 흥미로운 대화를 생성하려면 언어적 행동을 조작하기 위한 많은 매개 변수가 필요
    - 영화 대화에서 언어적 반사(특징)를 계산하여 캐릭터 언어 스타일의 말뭉치 기반 통계 모델을 개발한 다음, 이러한 모델을 사용하여 PERSONAGE 생성기의 매개 변수를 제어하는 것
    - 캐릭터 모델로 제어하고자 하는 PHONEAGE 매개변수는 아래 표 1에 표시   
      ![image](https://user-images.githubusercontent.com/49019292/223053372-f1a2d8e1-32ab-4e30-9a46-92681fff06d9.png)      
  - Corpus and Features
    - IMSDb 웹사이트의 862개의 영화 스크립트로 구성되어 있으며, 7400자, 총 664000줄의 대화와 9599000개의 토큰으로 이루어져있음
      - GENRE, DIRECTOR 및 YEAR 속성에 따라 문자 유형의 그룹을 정의
      - 예를 들어 펄프 픽션은 범죄, 드라마, 스릴러에 속함 
      - 캐릭터의 성별이 언어 스타일을 정의하는 요소가 될 수 있다고 생각하여 문자 성별 주석을 달음 
  - 아래 표 2는 feature sets이 나타나있음   
    ![image](https://user-images.githubusercontent.com/49019292/223053398-01b12f03-4514-4aa9-93c0-f0626add84b9.png)      
  - Dialogue Act features은 NPS Chat Corpus 1.0에서 훈련된 대화 행동 태그를 기반으로 함
  - 아래 그림 2는 실험의 흐름을 보여줌   
    ![image](https://user-images.githubusercontent.com/49019292/223053432-92700294-0b4a-4826-9546-1280b9e4e3fd.png)      
    - IMSDb(Internet Movie Script Database)에서 영화 스크립트를 수집
    - 각 영화 스크립트를 구문 분석하여 대화형 발화를 추출하여 각 영화의 정확히 한 캐릭터(예: 펄프 픽션 빈센트)의 발화를 포함하는 출력 파일을 생성 
    - 60회 이상 대화하는 사람 중에서 캐릭터를 선택
    - 각 캐릭터의 언어적 행동을 나타내는 특징을 추출
    - 모델은 이러한 특징들을 바탕으로 캐릭터 언어 스타일을 학습함
    - 캐릭터 모델을 사용하여 PERSONAGE generator의 파라미터를 제어함
    - 문자 모델을 사용하여 생성된 대화형 발화에 대한 인간 평가 실시
  - Character models
    - 파생된 샘플 문자 모델은 표 3에 제공   
      ![image](https://user-images.githubusercontent.com/49019292/223053467-6afb2ad4-8b2e-4ab4-ab29-00f21335a356.png)      
    - 표 4는 이러한 캐릭터 모델을 SpyFeet 발화에 적용한 결과를 보여주며, 현재 우리가 생산할 수 있는 변형 중 일부를 보여줌   
      ![image](https://user-images.githubusercontent.com/49019292/223053489-b891d9b6-298d-4073-832d-3eb67fab026d.png)      
-----------------------------------
- **실험 및 결과**
  - Experimental Setup
    - 목표는 문자 모델과 매핑을 테스트하는 것 
    - 인간에게 모방된 문자와 언어 스타일의 유사성 측면에서 다른 모델을 사용하여 생성된 일련의 발언을 평가하도록 요청하는 것
    - 먼저 영화에 쓰여진 애니 캐릭터와 같은 인식된 성격과 언어 스타일의 애니 모델을 사용하여 제작된 스파이 피트 캐릭터의 발화 성격의 유사성을 간접적으로 테스트하기 위해 실험을 설계
  - Experimental Results
    - 29명의 피험자(여성 13명, 남성 16명, 22세에서 44세)가 Web-based 실험에 참여 
    - 아래 표 5는 여섯 등장인물에 대한 Big Five Personality Scores의 TIPI 척도 판단의 평균 값을 보여줌   
      ![image](https://user-images.githubusercontent.com/49019292/223053507-10876f5a-9305-4e84-a7c0-d2e9dd863a92.png)      
    - 아래 표 6은 특정 캐릭터 모델로 제작된 발화와 원작 영화에서 그 캐릭터의 발화 사이의 평균 유사도 점수 판단   
     ![image](https://user-images.githubusercontent.com/49019292/223053520-c73e53e3-1035-4da9-8964-73b5e8849627.png)      
-------------------------------------------
- **고찰**
  - 영화 캐릭터는 성격이 뚜렷하게 드러나는 경우가 많아서 특징을 잡기 쉬울 것 같다고 생각했음!
  - 데이터셋이 제대로 수집이 된다면 캐릭터별 성격을 매우 잘 나타내는 데이터셋이 될 것 같다는 생각...
  - 오래된 논문이라서 그런지, 연구가 초반인 것 같은 느낌이 많이 들었음
  - 근데 내가 생성하는 문장은 말이 잘 안되는데 제시하는 예시들은 왜 다 괜찮은 것 같징...
  - 이 논문은 평가 방법이 인상 깊었음
    - 논문 주제가 영화 캐릭터의 성격을 학습해서 같은 성격의 캐릭터가 발화하는 것 같은 스토리를 만들어내기 때문에, 비교군이 존재함
    - 그렇기 때문에 원래 캐릭터의 발화와 같은 성격으로 생성된 문장을 비교하여 유사도를 구하는 것도 평가 방법이 될 수 있음
    - 대화 생성은 보통 비교군이 없는데... 
    - 소설 데이터셋도 소설 등장인물의 발화와 생성된 발화의 유사도를 측정하는 것도 하나의 방법이 될 수 있을 것 같다.
      - 캐릭터 중심으로 이야기를 생성하게 되면 이러한 평가 방법이 가능할 것 같다!
