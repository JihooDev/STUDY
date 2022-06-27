# MVC 패턴

## MVC (Model View Controller)

### MVC는 왜 탄생했을까?

예전 개발자들이 코드를 작성할 때 코드의 줄이 길어지다 보면 어디에 어느 코드가 있는지 찾는데 오래걸리고 한번 잘못되면 모든 코드를 갈아 엎어야 하는 경우가 발생했다. 한마디로 유지보수가 어려워 진 것이다. 그러다 프로그래머들이 코드를 계속해서 짜다보니 MVC 패턴으로 코드 구성을 하니 굉장히 효율적으로 코드를 작성하고 유지보수가 편해졌다. 그래서 MVC라는 패턴의 논문이 발표가 되고 지금도 많은 개발자들이 사용하는 디자인 패턴 중 하나이다.

### MVC 패턴의 흐름

![MVC패턴.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a35e2f1d-91a5-46c6-8620-6f2dc93223d9/MVC패턴.png)

1. 클라이언트는 “김지후” 라는 검색을 한다.
2. Controller 는 요청을 받고 Model에게 데이터를 요청하고 받는다.
3. Controller 는 View에게 받은 데이터를 전달한다.
4. View는 그 데이터를 이쁘게 Publishing 해서 다시 클라이언트에게 전달한다.
5. 클라이언트는 “김지후” 라는 데이터를 전달 받는다.

## Model View Controller 의 역할

### 1. Controller

- Model 과 View 를 이어주는 역할을 한다.
- 축구로 치면 미드필더의 역할에 가깝다

### 2. Model

- 데이터에 관련된 부분을 담당한다.
- 축구로 치자면 수비수에 가깝다 (data를 다루는 제일 중요한 역할이라고 생각한다.)

### 3. View

- 클라이언트가 편하게 요청한 데이터를 받아 볼 수 있도록 이쁘게 만든다.
- 클라이언트에게 보이는 UI와 Model로 부터 받은 data가 합쳐진 것이다.
- 축구로 치면 마무리를 담당하는 공격수 역할을 한다.

## MVC 규칙을 지키며 코딩하는 법

### 1. Model

- Model 은 Controller와 View에 의존하지 않아야 한다.
    - Model 내부에 Controller와 View의 코드가 있어서는 안된다.
    - data에 관련된 부분이다 보니 깔끔하게 데이터만 가져올 수 있게 코드를 섞지 않아야 한다.
    

### 2. View

- View는 Model에만 의존해야하며 Controller 에 관한 코드는 들어가면 안된다.
    - data를 받을 때는 사용자마다 다르게 보여줘야하는 data만 받아야 한다.
    

### 3. Controller

- Controller는 Model과 View 모두 의존이 가능하다.
    - 중개자 역할을 하며 전체 로직을 구성한다.
    - View가 Model로 부터 데이터를 받을 때 반드시 Controller를 거쳐서 받야아 한다.