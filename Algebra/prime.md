# Prime Number

A number which is divisible by 1 and itself is prime.

## Sieve of Eratosthenes

Sieve of Eratosthenes is an algorithm for finding all the prime numbers in a segment  $[1:n]$  using  $O(n \log \log n)$  operations.

### Code

```go
func getAllPrimeMap(n int) map[int]bool {

	// initialize
	isPrime := make([]bool, n+1)
	for i := range isPrime {
		isPrime[i] = true
	}

	// mark 0,1 as false
	isPrime[0], isPrime[1] = false, false

	// from 2 - n find primes
	for i := int64(2); i <= int64(n); i++ {
		if isPrime[i] && i*i <= int64(n) {
			for j := i * i; j <= int64(n); j += i {
				isPrime[j] = false
			}
		}
	}

	res := make(map[int]bool)
	for i := range isPrime {
		if isPrime[i] {
			res[i] = true
		}
	}

	return res
}

```
