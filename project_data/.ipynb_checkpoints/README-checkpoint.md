# Pohang Food Commerce Dataset

This folder contains the cleaned dataset for the team project:

> 포항 음식 상권 데이터 시각화 및 KMeans 기반 상권 유형 분석

## Expected outputs

- `pohang_all_stores_raw.csv`: all Pohang rows from the Gyeongbuk public file
- `pohang_food_stores.csv`: cleaned dataset for visualization and clustering
- `pohang_food_by_dong.csv`: dong-level category count/ratio table for clustering
- `pohang_food_stores_summary.txt`: basic validation summary
- `../docs/report_draft.docx`: report draft in Word format

## Current dataset summary

- Source file: 소상공인시장진흥공단 상가(상권)정보 경북 202603
- Pohang total rows: 27,997
- Pohang food rows after cleaning: 9,827
- Districts: 포항시 남구, 포항시 북구
- Dong count: 29

Category groups:

- 한식
- 분식/패스트푸드
- 카페/디저트
- 주점
- 중식
- 일식
- 양식/외국식
- 기타음식

## Main file columns

`pohang_food_stores.csv`

- `store_id`: 상가업소번호
- `store_name`: 상호명
- `branch_name`: 지점명
- `category_main_code`, `category_main`: 업종 대분류
- `category_mid_code`, `category_mid`: 업종 중분류
- `category_sub_code`, `category_sub`: 업종 소분류
- `category_group`: project-level simplified category group
- `sido`: 시도명
- `sigungu`: 시군구명
- `dong`: 행정동명
- `legal_dong`: 법정동명
- `address`: 지번주소
- `road_address`: 도로명주소
- `longitude`: 경도
- `latitude`: 위도

## For teammate B

Goal:

- 지도 시각화
- 행정동별 업종 구성비 그래프

Use:

- `pohang_food_stores.csv`

Important columns:

- `store_name`
- `category_group`
- `sigungu`
- `dong`
- `address`
- `road_address`
- `longitude`
- `latitude`

Suggested outputs:

- `pohang_food_map.html`
- `dong_top10_count.png`
- `dong_category_ratio.png`

Notes:

- There are 9,827 food rows, so plain Folium markers may be slow.
- Use `MarkerCluster` or `HeatMap` if the map is too heavy.
- For presentation slides, a map screenshot is enough.
- If the stacked bar chart is too crowded, show only the top 10 dongs by `total_count`.

## For teammate C

Goal:

- KMeans clustering
- PCA visualization
- Cluster interpretation

Use:

- `pohang_food_by_dong.csv`

Important columns:

- `sigungu`
- `dong`
- `total_count`
- columns ending in `_ratio`

Recommended features:

- `한식_ratio`
- `분식/패스트푸드_ratio`
- `카페/디저트_ratio`
- `주점_ratio`
- `중식_ratio`
- `일식_ratio`
- `양식/외국식_ratio`
- `기타음식_ratio`

Suggested outputs:

- `cluster_result.csv`
- `pca_cluster_plot.png`
- `cluster_profile.png`

Notes:

- Start with `k=3`.
- Compare with `k=4` only if the result is too broad.
- Do not use too many clusters because there are only 29 dongs.
- Cluster names should be decided after checking the actual result.
- Explain clustering as a trend analysis, not a correct-answer classification.

## Run from file data

```bash
python3 scripts/prepare_pohang_food_from_file.py "/path/to/소상공인시장진흥공단_상가(상권)정보_경북_202603.csv"
```

## API note

The API route was blocked by authentication issues during setup, so the project now uses the
official file dataset. This is more stable for the team project and preserves the same source
organization and column definitions.
