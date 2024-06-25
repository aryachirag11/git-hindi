# this is my readme

## subheading

### Install

```node
npm cloudinary
```

### create insantce

```javascript
const cloudinaru = require("cloudinary");
```

```cpp
void printArray(vector<int>& A){
  for(int i=0; i<A.size(); i++)
    cout<<A[i]<<" "<<endl;
}
```

### Best tiem to buy and sell stock

```cpp
class Solution {
public:
    int maxProfit(int k, vector<int>& prices) {
        int n = prices.size();
        // Initialize two 2D vectors with 0 to save space
        vector<vector<int>> curr(2, vector<int>(k + 1, 0));
        vector<vector<int>> next(2, vector<int>(k + 1, 0));

        // Iterate over each day in reverse order
        for (int i = n - 1; i >= 0; i--) {
            // Iterate over the two possible states: can buy (1) or cannot buy
            // (0)
            for (int canBuy = 0; canBuy <= 1; canBuy++) {
                // Iterate over the number of transactions limit from 1 to 2
                for (int limit = 1; limit <= k; limit++) {
                    int maxProfit = 0;

                    // If we can buy on the current day
                    if (canBuy) {
                        // Two choices: buy the stock or ignore
                        // Profit after buying the stock
                        int buyProfit = -prices[i] + next[0][limit];
                        // Profit if we ignore buying
                        int ignoreProfit = next[1][limit];
                        maxProfit = max(buyProfit, ignoreProfit);
                    }
                    // If we cannot buy (i.e., we have already bought and now we
                    // can sell)
                    else {
                        // Two choices: sell the stock or ignore
                        // Profit after selling the stock
                        int sellProfit = prices[i] + next[1][limit - 1];
                        // Profit if we ignore selling
                        int ignoreProfit = next[0][limit];
                        maxProfit = max(sellProfit, ignoreProfit);
                    }

                    // Store the result in curr array
                    curr[canBuy][limit] = maxProfit;
                }
            }
            // Update next array to be the current array for the next iteration
            next = curr;
        }

        // Return the maximum profit starting from day 0 with the ability to buy
        // and with 2 transactions allowed
        return next[1][k];
    }
};
```
