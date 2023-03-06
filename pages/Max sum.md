- Imperative solution
	- ```typescript
	  function maxConsecutiveSum(arr: number[]): number {
	  let maxSum = 0;
	  let currentSum = 0;
	    for (let i = 0; i < arr.length; i++) {
	      currentSum = Math.max(0, currentSum + arr[i]);
	      maxSum = Math.max(maxSum, currentSum);
	    }
	  
	    return maxSum;
	  }
	  ```
- Functional solution
	- ```typescript
	  function maxConsecutiveSum2(arr: number[]): number {
	    const reduceMaxSum = (state: { maxSum: number; currentSum: number }, currentNum: number) => ({
	      currentSum: Math.max(0, state.currentSum + currentNum),
	      maxSum: Math.max(state.currentSum + currentNum, state.maxSum)
	    });
	  
	    const { maxSum } = arr.reduce(reduceMaxSum, { maxSum: 0, currentSum: 0 });
	  
	    return maxSum;
	  }
	  ```