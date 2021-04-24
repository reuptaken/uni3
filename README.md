# uni3 - experiments with Uniswap v3

## lpmath.js

This is a port of https://github.com/Uniswap/uniswap-v3-periphery/blob/main/contracts/libraries/LiquidityAmounts.sol library to JavaScript. It doesn't use BigInt so maybe not suitable for precise calculations, but it's good enough for my purposes. I kept the same variable names even if all those `X96` probably doesn't make any sense in my implementation.

eg. usage

```
const lpMath = require('./lpmath.js')

const a = 1000
const b = 2000
const price = 1000

const sqrtRatioX96 = Math.sqrt(price)

const sqrtRatioAX96 = Math.sqrt(a)
const sqrtRatioBX96 = Math.sqrt(b)

const liquidity = lpMath.getLiquidityForAmounts(sqrtRatioX96, sqrtRatioAX96, sqrtRatioBX96, 1, 1000)
console.log(`Liquidity: ${liquidity}`)
for (let price = a - 50; price <= b + 50; price = price + 50) {
  console.log(price, lpMath.getAmountsForLiquidity(Math.sqrt(price), sqrtRatioAX96, sqrtRatioBX96, liquidity))
}
```
