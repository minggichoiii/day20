# day20
def max_score_stairs(n, stairs):
    if n == 1:
        return stairs[0]  # 계단이 하나일 경우, 그 계단의 점수를 반환
    elif n == 2:
        return stairs[0] + stairs[1]  # 계단이 두 개일 경우, 두 계단을 모두 밟는다

    # DP 배열 초기화
    dp = [0] * n
    dp[0] = stairs[0]  # 첫 번째 계단
    dp[1] = stairs[0] + stairs[1]  # 두 번째 계단까지 밟은 경우
    dp[2] = max(stairs[0] + stairs[2], stairs[1] + stairs[2])  # 세 번째 계단까지 밟은 경우

    # DP 점화식 적용
    for i in range(3, n):
        dp[i] = max(dp[i-2] + stairs[i], dp[i-3] + stairs[i-1] + stairs[i])

    return dp[n-1]  # 마지막 계단까지 도달할 때 얻을 수 있는 최댓값

# 입력 받기
n = int(input())  # 계단의 개수
stairs = [int(input()) for _ in range(n)]  # 각 계단의 점수

# 최대 점수 계산
result = max_score_stairs(n, stairs)

# 출력
print(result)
