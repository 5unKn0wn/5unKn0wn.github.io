---
layout: post
title: Addition and Subtraction over GF(2)
tags: Crypto
---

GF(2)에서의 뺄셈이 덧셈과 같은 이유를 알아보자.

GF(2)에서는 모듈로가 2이기 때문에 원소가 0, 1밖에 없다. (기약다항식이 x임)  
따라서 덧셈은

```
0 + 0 = 0
0 + 1 = 1
1 + 0 = 1
1 + 1 = 0
```

이기 때문에 GF(2)에서의 덧셈은 정수에서의 xor과 같게된다. (정확한 수식 증명은 아직 모르겠다.)  
여기서 뺄셈 역시 똑같이 xor로 표현되는데 GF(2)에서의 덧셈과 뺄셈이 같은 이유는 무엇일까?  

이에 대한 질문에 답하기 위해서는 뺄셈이라는 것이 정확히 어떠한 연산인지에 대해서 알아야한다.  
정수에서 x - y를 다르게 표현하면 x + (-y) 이다.  
이를 해석하면 x에서 y를 뺀다는 의미은 `x에 y의 덧셈에 대한 역원을 더한다`는 의미이다.  

덧셈에 대한 역원이란 `어떤 수에 더했을 때 0이 되는 수`를 의미한다. (여기서 0은 항등원을 의미하며 곱셈에 대한 역원도 있다.)  
그렇기에 정수 범위에서 y에 대한 역원은 무조건 -y 이다.  
y + (-y)는 무조건 0이기 때문이다.  

이걸 GF(2)에서 생각해보자.  
GF(2)에서 x - y를 하기 위해서는 y의 역원을 구해야 한다.  

그렇다면 GF(2)위에서의 역원은 어떻게 구해야할까?  
다시 말해서 GF(2)위에서 어떤 값에 더해서 0이 되는 수는 무엇일까?  
GF(2)위에서의 덧셈은 xor이라고 했다.  
그런데 서로 xor해서 0이 되는 값은??  
**자기 자신**이다.  
y xor y = 0이 되기 때문에 y의 덧셈에 대한 역원은 y 자기 자신인 것이다.  

y의 역원이 자기 자신이기 때문에 결국 x + y로 변해 뺄셈과 덧셈이 같게 되고  
이에 따라서 뺄셈 연산 역시 덧셈과 똑같이 xor로 연산하게 된다.