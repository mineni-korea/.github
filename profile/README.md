# 민이앤아이 코드 컨벤션

## 1. Pull Request 규칙
PR 및 커밋 메세지 제목은 작업 성격에 따라 **prefix**를 붙인다.  
- `feat:` 새로운 기능 추가  
- `fix:` 버그 수정  
- `refactor:` 코드 리팩토링
- `style:` 코드 스타일 수정
- `docs:` 문서 수정  
- `test:` 테스트 코드 관련 변경  

### 1-1. 제목 예시
✅ **Good**
```
feat: 사용자 로그인 API 추가
fix: DB 연결 에러 수정
refactor: ReportService 구조 단순화
```

❌ **Bad**
```
add login
버그 수정함
Update code
```

### 1-2. 본문 작성 규칙
- **PR 목적**을 명확히 설명 (예: 버그 수정, 기능 추가, 성능 개선, 리팩토링 등)  
- 관련 이슈가 있을 경우 연결:  
  ```
  closes #123
  resolves #456
  ```  
- UI 관련 변경사항이 포함될 경우 **스크린샷 첨부**  
  - Desktop, Mobile **둘 다 첨부**하여 반응형 테스트 용이하게 할 것  
  - 변경된 UI가 명확히 비교되도록 Before / After 형태 권장  

✅ **Good**
```
feat: 보고서 상세 페이지 UI 개선

- 보고서 상세 페이지에서 status 뱃지 색상 변경
- 불필요한 console.log 제거
- closes #42

[스크린샷 첨부]
Desktop: (before / after)
Mobile: (before / after)
```

❌ **Bad**
```
UI 바꿈
수정함
```

---

## 2. Import 순서
Import 구문은 **3rd party 라이브러리 → 내부 라이브러리** 순으로 작성한다.  

✅ **Good**
```ts
// 3rd party
import { useState } from "react";
import express from "express";

// my lib
import { ReportService } from "~/services/report.service";
import { formatDate } from "~/utils/date";
```

❌ **Bad**
```ts
import { ReportService } from "~/services/report.service";
import { useState } from "react";
import express from "express";
import { formatDate } from "~/utils/date";
```

---

## 3. 변수/함수 네이밍 (Typescript 한정)
- camelCase: 일반 변수, 함수명  
- PascalCase: 클래스, React 컴포넌트  
- UPPER_CASE: 상수  

✅ **Good**
```ts
const userName = "민이앤아이";
function getReportList() {}
class ReportController {}
const MAX_RETRY_COUNT = 3;
```

❌ **Bad**
```ts
const User_name = "민이앤아이";
function Get_report_list() {}
class reportcontroller {}
const MaxRetryCount = 3;
```

---

## 4. 코드 스타일
- 들여쓰기: 1 탭 (tab)
- 세미콜론 사용 필수  
- 불필요한 console.log 등 로깅 제거
- 추후 작업할 부분은 주석으로 `// TODO` 기재
- 주석은 쓴다면 **왜**를 설명, **무엇**은 코드로 드러나야 함

✅ **Good**
```ts
// 사용자의 포인트를 계산하는 로직
function calculateUserPoints(transactions: Transaction[]): number {
  return transactions.reduce((acc, t) => acc + t.amount, 0);
}
```

❌ **Bad**
```ts
// 포인트
function calc(t) {
  let a = 0;
  for (let i = 0; i < t.length; i++) {
    a += t[i].amount;
  }
  return a;
}
```
