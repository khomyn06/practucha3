Практична робота №3 Хомин Михайло
#include <stdio.h>

int main() {
    int p;
    scanf("%d", &p);

    long long dp[p+1][2][2];

    dp[1][0][0] = 1;
    dp[1][1][0] = 1;

    for (int i = 2; i <= p; i++) {
        dp[i][0][0] = dp[i][0][1] = 0;
        dp[i][1][0] = dp[i][1][1] = 0;
    }

    for (int i = 2; i <= p; i++) {
        dp[i][0][0] = dp[i-1][1][0] + dp[i-1][1][1];
        dp[i][0][1] = dp[i-1][0][0];

        dp[i][1][0] = dp[i-1][0][0] + dp[i-1][0][1];
        dp[i][1][1] = dp[i-1][1][0];
    }

    // Итоговый результат: сумма всех допустимых чисел длиной p
    long long result = dp[p][0][0] + dp[p][0][1] + dp[p][1][0] + dp[p][1][1];
    printf("%lld\n", result);

    return 0;
}
