# DSA-Important & Leetcode-Problems using Kotlin
1.Remove Element
    
   ```kotlin
    class Solution {
    fun main(){
        var nums = intArrayOf(2,3,2,3,4,6,6,5,4)
        var remove = 6
        var result = removeElement(nums, remove)
        println("The number of elements remaining: $result")
        println("after removing list:{$nums.slice(0 until $result)}" )
    }
        fun removeElement(nums: IntArray, remove: Int): Int {
            var k =0;
            for (i in nums.indices){
                if(nums[i] != remove){
                    nums[k] = nums[i]
                    k++
                }
            }
            return k
        }
    }
```

2.Kotlin: Sort an Array in Ascending Order 
      
   ```kotlin
            fun main() {
            // initilize the array
            val numbers = intArrayOf(2,1,2,8,5,6,3,2)
            val sortAcending = sortnumber(numbers)
            println("array int sorting : ${sortAcending.joinToString()}")
            }
    
            fun sortnumber(numbers: IntArray):IntArray{
                // read the size of array
                    val numSiz = numbers.size
                // read the array size + count
                    for (i in 0 until numSiz -1){
                // ensure that sholud not ready unnecessary 
                        for (j in 0 until numSiz-i-1 ){
                //check the number lesser than j
                            if (numbers[j]> numbers[j+1]){
                // swap the numbers
                                val temp = numbers[j]
                                numbers[j] = numbers[j+1]
                                numbers[j+1] = temp
                            }
                        }
                    }
                    return numbers
                }
```
3.Remove Duplicates from Sorted Array II

   ```kotlin 
    class Solution {
        fun removeDuplicates(nums: IntArray): Int {
        if(nums.size<= 2) return nums.size
        var i =2 
        for (j in 2 until nums.size){
            if(nums[j] !=nums[i -2]){
                nums[i] = nums[j]
                i++
                }
                }
        return i
    }
    }
```
4.Remove Duplicates from Sorted Array

   ```kotlin
    class Solution {
    fun removeDuplicates(nums: IntArray): Int {
        if(nums.size<=1) return nums.size
        var i =0
        for (j in 1 until nums.size){
            if(nums[j]!= nums[i]){
               i++
                nums[i] = nums[j]
            }
        }
        return i +1
    }
    }
```
5.To remove and print only non-prime numbers 

   
   ```kotlin
            fun main() {
    val number = intArrayOf(22,32,43,42,54,56,23,29)
    printNonPrimeNumbersFromArray(number)
      }
      fun printNonPrimeNumbersFromArray(nums: IntArray) {
          for (num in nums) {
              if (!checkprime(num)) {  // Check if the number is non-prime
                  print("$num ")    // Print non-prime numbers
              }
          }
      }
      
      fun checkprime(number: Int): Boolean{
          
         if (number<=1) return false
         
         for (i in 2..number / 2){
             
             if (number% i ==0){
                 
                 return false
             }
             
         }
          
          return true
      }
```

6.To rotate an array in Kotlin, we can shift the elements either to the right or to the left by a given number of positions. Let’s look at right rotations:
      
   ```kotlin
       class Solution {
       fun rotate(nums: IntArray, k: Int): Unit {
        var nsize= nums.size
        var rotation = k % nsize
         val rotationArray = nums.copyOfRange(nsize-rotation , nsize) + nums.copyOfRange(0, nsize - rotation)
        for (i in nums.indices){
            nums[i] = rotationArray[i]
           }
         }
       }
```

7.Max or min in given array
   ```kotlin
      fun main() {
          val myArray = intArrayOf(2,1,3,4,1,7)
          val min = myArray.minOrNull()
          val max = myArray.maxOrNull()
          println("$min. $max")
      }
   ```
using for loop
  ```kotlin
fun main() {
    val myArray = intArrayOf(2,11,3,4,0,-2,-1,7)
    var min = myArray[0]
    var max = myArray[0]
    for (num in myArray){
        if (num > max){
           max = num
        }
        if (num < min){
            min = num
        }
    }
    println("$min. $max")
}
```
8.Reverse an array using for loop

```kotlin
fun main() {
    val array = arrayOf("1","2","3","5")
   println(reversedArray(array).joinToString())
}
fun reversedArray(array: Array<String>):Array<String>{
    // Create a new array to store the reversed elements
   val revers = Array(array.size) {"0"}
    // Loop through the original array and fill the reversedArray from the end
   for(i in array.indices)
      revers[array.size -1 -i] = array[i]
    return revers
}
```

9.Two Sum with an Array (Simple Solution)

```kotlin
fun main() {
    val array = arrayOf(2, 7, 11, 15)
    println(reversedArray(array, 9))
}
fun reversedArray(array: Array<Int>, target: Int): Pair<Int, Int>?{
    var map = mutableMapOf<Int, Int>()
    for(i in array.indices){
     val comp = target - array[i]
     if(map.containsKey(comp)){
        return Pair(map[comp]!!, i)
     }
     map[array[i]]=  i
  }
    return null   
}
```
10.Merge Sorted Array

Solution Approach:
    Start from the end of both arrays (nums1 and nums2) and merge elements from the back to the front. This allows you to fill the nums1 array in place without needing additional space.

```kotlin
fun merge(nums1: IntArray, m: Int, nums2: IntArray, n: Int): Unit {
    var i = m - 1  // Last index of the valid portion of nums1
    var j = n - 1  // Last index of nums2
    var k = m + n - 1  // Last index of nums1 array

    // Compare elements from the end and place the largest at the end of nums1
    while (i >= 0 && j >= 0) {
        if (nums1[i] > nums2[j]) {
            nums1[k] = nums1[i]
            i--
        } else {
            nums1[k] = nums2[j]
            j--
        }
        k--
    }

    // If there are remaining elements in nums2, copy them
    while (j >= 0) {
        nums1[k] = nums2[j]
        j--
        k--
    }
}
```
11.majority element in the array
- Time Complexity: O(n), where n is the number of elements in the array. We only pass through the array once.
- Space Complexity: O(1), since we are using only a few variables.
   ```kotlin
  class Solution {
    fun majorityElement(nums: IntArray): Int {
        var n = 0
        var result = 0
        for (i in nums){
            if (n == 0){
                result = i
            }
            n += if(i == result) 1 else -1
        }
        return result
    }
  }
   ```
12. Best Time to Buy and Sell Stock
Edge Case:
    If the array is sorted in descending order (e.g., prices = [7, 6, 4, 3, 1]), there is no opportunity to make a profit, so the function will return 0.
Time Complexity:
    O(n), where n is the length of the array. We only pass through the array once.
Space Complexity:
    O(1), since we are only using two variables (minPrice and maxProfit).
    
 ``` kotlin
fun maxProfit(prices: IntArray): Int {
    var minPrice = Int.MAX_VALUE  // Start with a large number for the minimum price
    var maxProfit = 0             // To keep track of the maximum profit

    for (price in prices) {
        if (price < minPrice) {
            minPrice = price  // Update the minimum price
        } else {
            val profit = price - minPrice  // Calculate profit if sold at current price
            maxProfit = maxOf(maxProfit, profit)  // Keep track of the maximum profit
        }
    }
    return maxProfit
}
```
13.Reverse Words in a String
 ```kotlin
fun reverseWords(s: String): String {
    // Split the string into words and filter out any empty strings
    val words = s.split(" ").filter { it.isNotEmpty() }
    // Reverse the list of words and join them back into a string
    val reversed = StringBuilder()
    for (i in words.indices.reversed()) {
        reversed.append(words[i])
        if (i != 0) {
            reversed.append(" ")
        }
    }
    return reversed.toString()
}
fun main() {
    val inputString = "Hello world from OpenAI"
    val result = reverseWords(inputString)
    println(result)  // Output: "OpenAI from world Hello"
}
```
14. Length of the last string
```kotlin
class Solution {
    fun lengthOfLastWord(s: String): Int {    
        val word = s.trim().split(" ")
        return if (word.isNotEmpty()) word.last().length else 0
    }
}
```
15.Validate palindrom
-simple solution
```kotlin
class Solution {
    fun isPalindrome(s: String): Boolean {
    val filter = s.filter{
        it.isLetterOrDigit()
    }.toLowerCase() == filter.reversed()
    return filter == filter.reversed()
    }
}
class Solution {
    fun isPalindrome(s: String): Boolean {
   var left =0
   var right = s.length -1
  while(left < right){
    while((left < right) && !s[left].isLetterOrDigit()){
      left++
    }
    while((left < right) && !s[right].isLetterOrDigit()){
        right--
    }
    if(s[left].toLowerCase() != s[right].toLowerCase()){
        return false
    }
    left++
    right--  }
       return true
}}
```

