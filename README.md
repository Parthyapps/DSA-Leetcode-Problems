# DSA-Leetcode-Problems using Kotlin
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


