<data_clustering.ipynb>

workflow:
    1. 포항시 행정동별 8개 업종 비율을 정리한 'pohang_food_by_dong.csv' 데이터 가져오기.
    2. 행정동 이름(label로 사용) 과 업종 비율(X, features)로 분리
    3. 데이터 X, 정규화
    4. KMeans clustering 적용 (k=3으로 분석)
    5. PCA 차원 축소 (8d->2d for plotting)
    6. 결과 출력 (PCA cluster 산점도, cluster별 업종 분석, 분석한 df 테이블 내보내기)

Todo:
1. PC값과 이에 따른 cluster가 갖는 의미 분석(업종 비율을 통한 상권 분석. ex. 핫플레이스 상권, 전통적 식당 상권, ...)
2. 실제 포항시 지역의 특성과 분석 결과를 연결해보기
3. etc...