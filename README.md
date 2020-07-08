## CEO 인터뷰에서 관측할 수 있는 남성성과 주가 변동폭 간 상관관계


20.03 ~ 20.07 글로벌경영학과 김영한 교수님 Research Assistant 작업.


착안점

* 남성성은 테스토스테론과 관련이 있으며, 위험을 감수하고 도전하려는 성향과 관련이 있다.
* 기업의 CEO가 Risk-taking 성향이 강하다면, 해당 기업의 주가 변동폭 (return Volatility)은 클 수 있다.
* 일반적으로 테스토스테론 수치가 높을수록 남성의 목소리 톤은 낮아진다.

-> 그렇다면, CEO 인터뷰로 관측되는 Pitch와 해당 기업의 주가 변동폭의 상관관계는?


교수님이 제공한 870여 개의 CEO 인터뷰 파일 (.wav)

---

### parselmouth 사용법


https://parselmouth.readthedocs.io/en/stable/api_reference.html#parselmouth.Formant

get_formant.ipynb 참고. 이 노트북 파일은 colab에서 실행하였음.


음원분석 프로그램으로는 C++ 기반의 Praat이 있지만, Python Wrapper 라이브러리인 parselmouth를 사용했다.

parselmouth 라이브러리는 공식 docs의 설명을 제외하면 아무런 예시나 설명이 없다.

1. 음원파일에서 Pitch나 Formant값을 추출하려면, 음원파일을 먼저 Sound 객체로 변환해야 한다.
2. Sound객체로 변환한 파일을 to_formant, to_pitch 함수로 각각 Formant, Pitch 객체로 변환한다.
    * Praat에서 formants를 구하기 위해 분절한 시간단위는 ts()함수로 확인할 수 있다.
3. 각각의 객체에서 필요한 함수를 사용한다.
    * F1 ~ F5까지의 값을 구하기 위해 Formant객체의 get_value_at_time 함수를 사용한다. F1 ~ F5 값을 구하려면 get_value_at_time의 파라미터로 F1 ~ F5에 해당하는 문자열값을 넣어야 한다.
    * Pitch 객체의 to_pitch()함수로 Pitch값을 구할 수 있다.
    

        
    