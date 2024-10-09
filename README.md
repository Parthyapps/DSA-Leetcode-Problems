# DSA-Leetcode-Problems using Kotlin
1.Remove Element
~~~kotlin
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
} ~~~
