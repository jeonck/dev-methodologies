## 동기와 비동기의 예시 코드 및 출력 결과

동기(Synchronous)와 비동기(Asynchronous)의 차이를 이해하기 위해, 각각의 예시 코드와 그 출력 결과를 함께 살펴보겠습니다.

### 동기(Synchronous) 예시

동기 방식에서는 각 작업이 순차적으로 실행되며, 이전 작업이 완료될 때까지 다음 작업이 대기합니다.

**예시 코드**:

```javascript
console.log("1. 시작"); // 1번 로그 출력

const sum = 1 + 2; // 덧셈 연산
console.log("2. 덧셈 결과:", sum); // 2번 로그 출력

console.log("3. 종료"); // 3번 로그 출력
```

**출력 결과**:
```
1. 시작
2. 덧셈 결과: 3
3. 종료
```

이 코드에서는 각 로그가 순차적으로 출력되며, 모든 작업이 완료된 후에 다음 작업이 진행됩니다.

### 비동기(Asynchronous) 예시

비동기 방식에서는 작업을 시작하고, 결과를 기다리지 않고 다음 작업을 수행합니다. 이로 인해 여러 작업이 동시에 처리될 수 있습니다.

**예시 코드** (setTimeout 사용):

```javascript
console.log("1. 시작"); // 1번 로그 출력

// 2초 후에 콜백 함수를 실행하는 비동기 코드
setTimeout(() => {
    console.log("2. 2초 후 실행"); // 3번 로그 출력 (2초 후)
}, 2000);

console.log("3. 종료"); // 2번 로그 출력
```

**출력 결과**:
```
1. 시작
3. 종료
2. 2초 후 실행
```

이 코드에서는 "1. 시작"과 "3. 종료"가 먼저 출력되고, 2초 후에 "2. 2초 후 실행"이 출력됩니다. 비동기 작업이 메인 스레드를 차단하지 않기 때문에, 다음 작업이 즉시 실행됩니다.

### 비동기 예시 (Promise 사용)

비동기 작업을 Promise를 사용하여 처리하는 예시입니다.

**예시 코드**:

```javascript
console.log("1. 시작"); // 1번 로그 출력

// 비동기 작업을 수행하는 프로미스 생성
const promise = new Promise((resolve) => {
    setTimeout(() => {
        resolve("2. 프로미스 결과"); // 프로미스를 resolve 상태로 변경
    }, 2000);
});

// 프로미스가 resolve 상태가 되면 then() 안의 콜백 함수 실행
promise.then((result) => {
    console.log(result); // 3번 로그 출력 (2초 후)
});

console.log("3. 종료"); // 2번 로그 출력
```

**출력 결과**:
```
1. 시작
3. 종료
2. 프로미스 결과
```

이 예시에서도 비동기 작업이 메인 스레드를 차단하지 않으며, Promise가 완료된 후에 결과가 출력됩니다.

### 결론

동기와 비동기의 차이는 작업 처리 방식에 있으며, 동기는 순차적으로 실행되고 비동기는 동시에 여러 작업을 처리할 수 있습니다. 이러한 차이를 이해하면, 프로그래밍에서 적절한 방식을 선택하는 데 도움이 됩니다[2][4][8].  

#### 비동기와 동기가 필요한 경우 
비동기는 I/O 작업이 많은 경우에 쓰는 것이 좋습니다.  
REST API 호출이나 웹 크롤러 등 네트워크 요청 처리가 많은 경우  
대용량 파일 처리나 비동기 로그 저장 등 파일 입출력을 다루는 경우  
비동기 DB 드라이버를 사용해 DB를 연결하는 경우  
채팅 서버 등에서 수많은 동시 다중 작업을 처리하는 경우  

[1] https://young-taek.tistory.com/230?category=703288
[2] https://bloghelloworld.tistory.com/649
[3] https://bbangson.tistory.com/61
[4] https://velog.io/@pgunoya/%EB%B9%84%EB%8F%99%EA%B8%B0-%ED%95%A8%EC%88%98%EC%9D%98-%EC%98%88%EC%8B%9C
[5] https://docs.oracle.com/cd/E13203_01/tuxedo/build21/active/tasks4.htm
[6] https://blog.naver.com/ghdalswl77/222438273191?viewType=pc
[7] https://velog.io/@ellie12/%EC%98%88%EC%8B%9C%EB%A1%9C-%EB%B3%B4%EB%8A%94-%EB%B9%84%EB%8F%99%EA%B8%B0
[8] https://inpa.tistory.com/entry/%F0%9F%91%A9%E2%80%8D%F0%9F%92%BB-%EB%8F%99%EA%B8%B0%EB%B9%84%EB%8F%99%EA%B8%B0-%EB%B8%94%EB%A1%9C%ED%82%B9%EB%85%BC%EB%B8%94%EB%A1%9C%ED%82%B9-%EA%B0%9C%EB%85%90-%EC%A0%95%EB%A6%AC
[9] https://www.geeksforgeeks.org/javascript/synchronous-and-asynchronous-in-javascript/
[10] https://nicehyun12.tistory.com/45
[11] https://www.ramotion.com/blog/synchronous-vs-asynchronous-programming/
[12] https://inpa.tistory.com/entry/%F0%9F%8C%90-js-async
[13] https://khuang159.medium.com/javascript-asynchronous-synchronous-72d4f13fba5d
[14] https://www.datoybi.com/asynchronous-js/
[15] https://www.freecodecamp.org/news/synchronous-vs-asynchronous-in-javascript/
[16] https://springfall.cc/article/2022-11/easy-promise-async-await
[17] https://distantjob.com/blog/synchronous-vs-asynchronous-programming/
[18] https://stackoverflow.com/questions/31835121/return-value-in-a-synchronous-function-after-calling-asynchronous-function-seti
[19] https://docs.tosspayments.com/blog/async-await-example
[20] https://refine.dev/blog/synchronous-vs-asynchronous/
[21] https://learn.microsoft.com/en-us/answers/questions/1291792/how-to-call-an-async-method-synchronously-in-c
[22] https://www.reddit.com/r/swift/comments/1e5tlsp/accessing_results_of_asynchronous_code_in_a/
[23] https://velog.io/@songyi7091/%EB%8F%99%EA%B8%B0-%EB%B9%84%EB%8F%99%EA%B8%B0
[24] https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest_API/Synchronous_and_Asynchronous_Requests
[25] https://stackoverflow.com/questions/55647753/call-async-function-from-sync-function-while-the-synchronous-function-continues/71489745
[26] https://tech-monster.tistory.com/180
[27] https://kenel.tistory.com/105
[28] https://velog.io/@ksh9409255/%EB%8F%99%EA%B8%B0%EB%B9%84%EB%8F%99%EA%B8%B0
[29] https://kangworld.tistory.com/25
[30] https://webheck.tistory.com/entry/Java%EB%8F%99%EA%B8%B0%EC%99%80-%EB%B9%84%EB%8F%99%EA%B8%B0-%EB%B0%A9%EC%8B%9DAsynchronous-processing-model
[31] https://www.mendix.com/blog/asynchronous-vs-synchronous-programming/
[32] https://stackoverflow.com/questions/74703727/how-to-call-async-function-from-sync-funcion-and-get-result-while-a-loop-is-alr
[33] https://dev.to/chucks1093/synchronous-vs-asynchronous-programming-in-javascript-9d3
[34] https://softwareengineering.stackexchange.com/questions/433640/in-javascript-how-is-awaiting-the-result-of-an-async-different-than-sync-calls
