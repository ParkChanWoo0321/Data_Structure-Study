# 알고리즘 실습 정리 (C) 📌

분할 정복(Divide & Conquer)과 동적 계획법(Dynamic Programming) 기반 알고리즘을 C로 구현한 코드입니다.

---

## 1) 분할 정복: 최대 구간 합(Maximum Subarray Sum)

### ✅ 구현 내용
- 배열에서 **연속된 부분 배열의 합이 최대가 되는 값**을 구합니다.
- 방법: 분할 정복
  - 구간을 `mid` 기준으로 나눈 뒤
    1) 왼쪽 구간의 최대 구간 합  
    2) 오른쪽 구간의 최대 구간 합  
    3) **mid를 가로지르는 최대 구간 합**(cross sum)  
  - 위 3개 중 최대값을 선택합니다.

### 핵심 함수
- `maxCrossSum(arr, left, mid, right)`
  - `mid`에서 왼쪽으로 누적하며 최대 합(`leftSum`)
  - `mid+1`에서 오른쪽으로 누적하며 최대 합(`rightSum`)
  - 반환: `leftSum + rightSum`
- `maxSubArraySum(arr, left, right)`
  - 재귀적으로 좌/우/교차 최대값을 계산 후 최댓값 반환

### 시간 복잡도
- 재귀식: `T(n) = 2T(n/2) + O(n)`
- 결과: **O(n log n)**

---

## 2) 동적 계획법: 모든 정점 쌍 최단 경로(Floyd-Warshall)

### ✅ 구현 내용
- 그래프의 모든 정점 쌍 `(i, j)`에 대해 **최단 거리**를 구합니다.
- 방법: Floyd-Warshall (DP)
  - 중간 정점 `k`를 하나씩 허용해가며 거리 갱신
  - 점화식:
    - `dist[i][j] = min(dist[i][j], dist[i][k] + dist[k][j])`

### 구현 포인트
- `INF`를 큰 값으로 두어 **경로 없음**을 표현
- 3중 반복문 구조:
  - `for k` → `for i` → `for j`
- 최종적으로 `dist` 행렬이 모든 쌍 최단거리 결과가 됨

### 시간 복잡도 / 공간 복잡도
- 시간 복잡도: **O(n³)**
- 공간 복잡도: **O(n²)** (거리 행렬)

---
