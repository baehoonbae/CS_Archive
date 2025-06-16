# 브라우저 렌더링 과정

## 개요

대부분의 브라우저는 싱글 쓰레드이기 때문에, 메인 쓰레드가 요청된 모든 작업을 수행하면서도 유저와의 상호작용에 반응 할 수 있도록 보장하기 위해서는 렌더링 시간이 중요합니다.
브라우저의 메인 쓰레드의 책임을 줄여주는 방식으로 웹 성능 향상을 이루면 렌더링은 부드럽고 상호작용에 대한 응답은 즉각적으로 나타나게 될 것입니다.

## 핵심 개념

> 브라우저 렌더링 과정은 크게 5가지 단계 (Parsing, Style, Layout, Paint, Composite)로 나눌 수 있습니다.

### 1. Parsing

브라우저는 파싱을 통해서 HTML 파일을 해석하여 DOM Tree를 구성하는데 HTML에 CSS가 포함되어 있다면 파싱을 통해 CSSOM Tree 작업도 함께 진행합니다.

### 2. Style

스타일 단계에서는 DOM Tree와 CSSOM Tree를 결합시켜서 렌더링을 위한 Render Tree를 구성합니다.

`Render Tree`는 **브라우저 화면에 보여지지 않는 것들은 포함하지 않습니다.**

예를 들어, `display: none`과 같은 속성은 공간을 차지하지 않기 때문에 Render Tree에서 제외됩니다.

### 3. Layout

레이아웃 단계에서는 Render Tree를 화면에 배치하기 위해 정확한 위치와 크기를 계산합니다.

루트부터 노드를 순회하면서 노드의 위치와 크기를 계산해서 렌더 트리에 반영합니다.

### 4. Paint

페인트 단계에서는 앞서 계산된 값을 이용하여 각 노드들을 화면 상의 실제 픽셀로 변환합니다.

이때 변환된 결과는 여러 개의 레이어로 관리됩니다.

쉽게 말해, 브라우저 화면에 **픽셀을 렌더링하는 과정**이라고 할 수 있습니다.

### 5. Composite

컴포지트 단계에서는 Paint 단계에서 생성된 레이어를 합성하여 실제 화면에 나타냅니다.

이러면 이제 화면에서 웹 페이지를 확인할 수 있습니다.

## 참고 자료

- https://developer.mozilla.org/ko/docs/Web/Performance/Guides/How_browsers_work
- https://enjoydev.life/blog/frontend/2-browser-rendering
