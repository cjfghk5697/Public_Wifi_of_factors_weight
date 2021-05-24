# Public_Wifi_of_factors_weight
<hr>
# 공공와이파이 요인 데이터 분석 방법
연구는 면적, 지역 총생산, 인구가 지역별 보급대수에 영향을 주는지 확인하기 위한 것이다. 그래서 다중공선성(Multicollinearity)이 있는지 VIF(Variance Inflation Factors)를 이용해 구해볼 것이다.
VIF는 Python 라이브러리를 이용해 그래프로 구현하며 값을 가져온다. 그래서 도출된 값들을 종합하여 면적, 지역 총생산, 인구가 보급대수에 영향을 끼치는 순으로 배열할 것이다.  
<hr>
# 분석 과정
![image](https://user-images.githubusercontent.com/80466735/119354259-d4918400-bcde-11eb-8480-3cb0080a2540.png)

CSV파일에 인구 population, 지역 area, 지역별 총생산GDP in region, 설치대수 installed, 사용량 use(TB) , 사용자 수 user(10000) 엑셀 파일을 만들었다.

![image](https://user-images.githubusercontent.com/80466735/119354279-da876500-bcde-11eb-918c-87e57549e9ce.png)

산점도 그래프를 만들어서 다중공선성이 있는지 확인해본다. 1행 2열은 Population(인구)와 Area(지역)간 1:1 상관관계이다. 본다면 양의 상관관계가 있음을 확인할 수 있다. 하지만 서울, 부산과 같은 면적에 비해 높은 인구수를 가진 지역이 있기 때문에 점이 흩어져 있다. 1행 3열은 GDP in Region(지역내 총생산)과 Population(인구)간 1:1 상관관계이다. 양의 상관관계가 뚜렷하게 보인다. 2행 3열은 GDP in region(지역내 총생산)과 area(지역 크기)간의 1:1 상관관계이다. 그래프를 보면 양의 상관관계인지 알기 힘들다. 그래프가 흩어짐이 심하다. 

![image](https://user-images.githubusercontent.com/80466735/119354295-e1ae7300-bcde-11eb-89d6-16c54857546d.png)
![image](https://user-images.githubusercontent.com/80466735/119354303-e2dfa000-bcde-11eb-9632-8c5788376dd3.png)

OLS(최소제곱법)을 이용하여 coef(기울기)를 구한다. Population의 coef는 -0.0011로 installed(설치대수)와 음의 상관관계가 있다. 하지만 굉장히 미세하게 관련이 있다. Area는 -0.1556로 설치대수와 음의 관계에 놓여있다.
GDP in region이 0.0306으로 특이하게도 양의 관계에 놓여있다. 다른 인구나 지역, 크기는 음의 상관관계인 반면 경제가 와이파이 보급 대수에 영향을 준다.

그리고 VIF를 적용해서 값을 도출해본 결과 값의 차이가 없다. 

# 분석 결과
다중공선성이 있는지 확인하기 위해 VLS를 사용해서 OLS를 도출한 결과 경제적 요건만이 양의 상관관계에 있다. 그리고 나머지는 음의 상관관계에 놓여있다. 그중 인구는 큰 영향을 주지 못한다는 점을 알수가 있었다. 그중 면적이 가장 큰 영향을 준다. 하지만 면적은 계속해서 유지가 되기 때문에 유의미한 값이라고 볼 수 없다. 결론적으로 지역 내 총 생산이 값이 바뀌고 양의 영향을 끼치는 것을 알 수 있었다.

<hr>
# 여담
간단한 분석을 위해 pandas profiling도 사용해봤다. 근데 데이터 값이 이상하게 나온다.( 분석 내용은 이 문서안에 담겨 있다.)

# 자세한 정보
공공와이파이 데이터 분석과 사회적으로 어떻게 해야할지 적어 놓은 글이다. 단순히 데이터를 분석하는데서 끝내는 건 별 의미가 없다. 그래서 분석한 자료를 기반으로사회적 긍정적, 부정적 영향을 정리했다. 그다음 어떤 태도를 지니고 정책을 나아가야 할지 적어놨다. 시간이 난다면 읽어보길 바란다.
[공공와이파이 데이터 분석.docx](https://github.com/cjfghk5697/Public_Wifi_of_factors_weight/files/6532603/default.docx)
