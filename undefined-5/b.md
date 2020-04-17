# 자기개발

1.  비지니스 네트워크
   1. 많을수록 좋다
2. 자산
   1. 저작권
   2. 디지털로 표현할수있는것들도 포함
   3. 물질적인것들도
3. 거래
4. 스마트컨트렉트





특징

1.  탈중앙화
2. 공정성





1.  시간단축
   1. 각종 서류 확인해야하는걸 줄인다
   2.  실시간으로 트랙킹되어 바로바로 접근할 수 있다.
      1. 

## 변대리님께 지적받은사항

1. Html Wrapper 네이밍 \(용도-타입\)
   * wrapper-어쩌구
   * box-어쩌구
   * article-어쩌구
   * aisde-어쩌구
   * btn-어쩌구
2. css 클래스 첫글짜는 숫자 절대 금지
3. button 태그에는 반드시 type
4. 햄버거는 span 대신 i 태그로
   * i -&gt; 아이콘의 약자로 쓰임
5.  안에는 반드시 헤딩이 있어야 좋음
   * h1, h2, h3...
6. css 기능만으로 left, right 클래스를 나눌때는 nth-child 쓴다
   * nth-child\(odd\)
   * nth-child\(even\)
7. article
   * 광고영역, 뉴스 기사 영역 등등에 쓰임..
8. sgv 태그를 쓸때는 blind 테그로 감싼다

```css
.blind {
    position: absolute;
    clip: rect(0 0 0 0);
    width: 1px;
    height: 1px;
    margin: -1px;
    overflow: hidden
}
```

