Fast Campus Data Science School 17th <EDA project>
## ✨The Analysis of Consumption & Commercial District in Jeju✨

![jeju](https://user-images.githubusercontent.com/71582831/112963369-438ca980-9182-11eb-8ad6-e5dcee3ab197.jpg)


## 📜Reference
### API 
  #### 1. 제주도 내국인 관광객 지역, 업종, 성별, 연령대별 카드 이용 데이터 API
    - 출처: 제주데이터랩 (https://www.jejudatahub.net/data/view/data/597)
    - 내용: columns = [일자, 시군구, 읍면동, 업종명, 관광객구분(제주도민/내국인관광객), 연령대, 성별, 이용자수, 이용횟수, 이용액]
    - 기간: 2017.01.01 ~ 2018.12.31
    - 목적: 제주도민과 관광객을 구분하여 지역별/업종별 결제액 및 bill 단가 비교

  #### 2. 카카오 지도 API
    - 출처: kakao developers (https://developers.kakao.com/product/map)
    - 내용: pyproj 활용, ITRF2000 기준 좌표계를 경도/위도 기준값으로 변환
    - 목적: 지도 시각화를 위한 정확한 좌표값 확인 및 데이터셋 간 기준 통일

### Data
  #### 1. 공간정보 탐색적 데이터 분석 경진대회
    - 출처: Dacon (https://dacon.io/competitions/official/235682/data/)
    - 내용: columns = [기준년월, 시군구, 소상공인구분, 업종명, 시간대, 총사용금액, 재난지원금 사용금액, 총 이용건수]
    - 기간: 2020.05.01 ~ 2020.08.31
    - 목적: 지역별/시간대별 상세 업종 결제액 분석
    ※ 비고
      * 본 데이터는 API 1번과 비슷한 항목이 있으나 보다 상세한 업종 분류 제공(205개)
      * API 1번과 달리 ITRF2000 기준 좌표 기준으로, API 2번 활용하여 경도/위도 기준으로 변환
  #### 2. KCB 금융스타일 시각화 경진대회 (jeju_financial_life_data)
    - 출처: Dacon (https://dacon.io/competitions/official/82407/overview/description/)
    - 내용: columns = [신우편번호, 기준년월, 경도, 위도, 성별, 연령대, 직업군별 비중, 소득, 소비액, 부채, 신용도, 부동산, 차량]
    ※ columns 상세 설명: (https://dacon.io/competitions/official/82407/talkboard/400772?page=1&dtype=recent)
    - 기간: 2019.02.01 ~ 2019.02.28
    - 목적: 소득, 주택보유수, 부채, 직업 등 요소별 상관관계 분석 및 지도를 활용한 시각화

---

## ✒Hypotheses
#### 1. Hotels in Jeju
- 제주도 내 숙박 업종 분포

Type  |        Spent Num Ranking   |   Total Spent Ranking   
------------ | ---------------- | ----------------
특급 호텔 | 2 | 1
기타 숙박업 | 1 | 2
2급 호텔 | 3 | 3
1급 호텔 | 4 | 4
    
    
    ▶ 1급 호텔의 이용객이 가장 적은 이유는 특급 호텔과 2급 호텔의 호텔 bill 단가를 비교했을 때 가격 차이가 크지 않기 때문이다.
    ▶ 1급 호텔이 관광객 주 소비지역과 가까이 위치하지 않을 것이다.
    ▶ 다른 숙박업종에 비해 군집을 이루지 않았을 가능성이 있다.
    
#### 2. Correlation of Income & jobs & Debt
    ▶ 제주도민의 소득, 직업(대기업,중소기업, 자영업 등), 부채, 신용도는 양의 비례 관계를 가질 것이다.

#### 3. Correlation of Income & Residential area
    ▶ 소득 수준이 비슷한 사람들은 비슷한 지역에 거주하며 군집을 이룰 것이다.
    ▶ 소득 수준이 높은 지역의 소매업과 요식업의 bill 단가는 소득 수준이 낮은 지역에 비해 더 높을 것이다.

#### 4. Regional distribution by industry
    - A: 제주도민과 외부 관광객들이 모두 고루 사용하는 업종
    - B: 외부 관광객 매출에 의존도가 높은 업종 (ex: 면세점, 주점업, 호텔업, 골프장, 자동차 임대업 등)
    ▶ A와 B 업종의 지역 분포는 상이할 것이다.
    ▶ A는 제주도 전역에 고루 위치하고 있는 반면에 B는 해당 업종끼리 군집을 이루고 있을 것이다.
