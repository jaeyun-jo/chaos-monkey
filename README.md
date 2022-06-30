# chaos-monkey
chaos monkey를 활용한 분산 시스템 신뢰성 테스트 


chaos monkey 활성화 확인
(GET) /actuator/chaosmonkey/status


Ready to be evil!
or

You switched me off!
chaos monkey enable/disable
(POST) /actuator/chaosmonkey/enable
(POST) /actuator/chaosmonkey/disable 
chaos monkey watcher 확인
(GET) /actuator/chaosmonkey/watchers

chaos monkey assults 확인
(GET) /actuator/chaosmonkey/assaults

(POST) /actuator/chaosmonkey/assaults

{ "level" : 3, "latencyActive" : true, "latencyRangeStart" : 2000, "latencyRangeEnd": 5000 }
: 3번에 한번씩 2초~5초 사이의 지연 공격 


{ "level" : 3, "exceptionsActive" : true, "exception.type": "java.lang.RuntimeException" }
: 3번에 1번씩 RuntimeException 발생  


{ "killApplicationActive" : true,  "runtimeAssaultCronExpression" : "0 0/1 * * * ?" }
: cronExpression에 걸리면 application kill 


{ "memoryActive": true, "memoryMillisecondsHoldFilledMemory": 5000, "memoryFillTargetFraction": 0.95,  "runtimeAssaultCronExpression": "0/10 * * * * ?" }
: 메모리의 95%를 10초 간격으로 5초 홀딩 
