---
layout: post
title:      "Prime Number Test"
date:       2018-03-26 19:14:42 +0000
permalink:  prime_number_test
---


So one of the labs I did recently required us to create a method, #prime?, that takes an integer argument, returns true if the integer is prime, and false if it is not. We also could not require the "Math" (or any other) libraries in creating our solution. 
After poking around on Google for a bit, I found an approach that I wanted to implement. This particular test is a pretty basic trial-by-division method, but with a careful selection of our possible divisors to try -- all known primes between 2 and the square root of our number. This yielded two key issues for my program though: 

1. I needed a list of known primes
2. I needed to be able to take the square root of a number 


Including an array of known primes would very quickly make my program lengthy and ugly. I'm really hoping to make a fairly concise program here, so that throws out including a lengthy list of known primes. I also can't take the square root of the argument since I can't use the math library. 
For my first attempt, I did end up using a list of known primes up to 97, since that fit on one line and wasn't too unsightly. 

```
def prime?(number)
  return false if number <= 1
  primes_to_100 = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97]
  return true if primes_to_100.include?(number)
  primes_to_100.each{|prime| return false if number % prime == 0}
  true
end
```

This worked, but only reliably for primes up to 97^2, 9409 -- not super useful! I knew I needed more functionality and a wider usability to feel like I actually did anything worthwhile, so I looked up what some other students did on github. This led me to an improvement on my above test that (hopefully!) worked reliably for primes above 9409 and reduced the benchmark test. After a few tests and tweaks, I arrived at the following:

```
def prime?(number)
  return true if number == 2
  return false if number <= 1 || number.even?
  poss_divisors = ((3..(number - 1)/2).select{|num| num.odd?}).to_a
  !poss_divisors.any? { |div| number % div == 0 }
end
```

The first line inside the method handles an edge case that would be missed by the next line, which returns false for 0, negative integers, and integers divisible by 2.  The third line creates an array of possible divisors, all odd numbers (since we eliminated multiples of 2) from 3 to half of our test number. The final line checks if our test number can be divided cleanly (remaineder 0) by any of the numbers in the array of possible divisors we created on line three. 

The results:

Since my first attempt cannot be trusted to be reliable for tests above 9409, I'll just be comparing the benchmark measurements for my final solution vs. the Learn.co solution branch on github. I used a few known primes and one known composite. You can see the code and results here: https://github.com/AspenJames/prime_number_test
My method in `final_test.rb` runs in general two times faster than the Learn.co provided solution while also being four lines shorter. 

I really enjoyed making adjustments to my code and seeing the real-time results in the benchmark tests.  This was great practice on writing concise and efficient code. 



