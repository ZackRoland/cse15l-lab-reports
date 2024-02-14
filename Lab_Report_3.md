#**LAB 3**
---
## **Part 1-Bugs**
> The bug of focus for this part is for the reverseInPlace method in ArrayExamples
1) A failure Inducing input:
```
int[] input2 = {1,2,3};
ArrayExamples.reverseInPlace(input2);
assertArrayEquals(new int[] {3,2,1}, input2 );

```
2) A non failure inducing input:
```
int[] input1 = { 3 };
ArrayExamples.reverseInPlace(input1);

```  
3) Symptom from running tests:
```
1) testReverseInPlace(ArrayTests)
arrays first differed at element [2]; expected:<1> but was:<3>
    	at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
    	at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
    	at org.junit.Assert.internalArrayEquals(Assert.java:534)
    	at org.junit.Assert.assertArrayEquals(Assert.java:418)
    	at org.junit.Assert.assertArrayEquals(Assert.java:429)
    	at ArrayTests.testReverseInPlace(ArrayTests.java:16)
    	... 32 trimmed
Caused by: java.lang.AssertionError: expected:<1> but was:<3>
    	at org.junit.Assert.fail(Assert.java:89)
    	at org.junit.Assert.failNotEquals(Assert.java:835)
    	at org.junit.Assert.assertEquals(Assert.java:120)
    	at org.junit.Assert.assertEquals(Assert.java:146)
    	at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
    	at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
    	... 38 more

```
4) The Bug:
Before:
```
static void reverseInPlace(int[] arr) {
   for(int i = 0; i < arr.length; i += 1) {
     arr[i] = arr[arr.length - i - 1];
   }
 }

```
Explanation of Bug:
> The reason for the bug was that it was changing the orginal array while looping so when
> {3 , 2, 1} was reversed, when staring at 0, arr[0] was set to arr[arr.length-i-1] so arr[2] which is correct
> but as the loop continues, a problem will inevitagbly arise. arr[1] will be set to arr[1] which is also correct
> but when we get to arr[2], arr[2] will be set to arr[0] but we already set arr[0] so arr[2] will get set to the same
> value as arr[0] resulting in an array of {3,2,3} instead of {3,2,1} that we were initally looking for. The araay {3}
> wouldn't have resulted in a bug since there wasn't enough elements in the array to allow for that mismatchup.
After:
```
static void reverseInPlace(int[] arr) {
   int[] tempArr = new int[arr.length];
   for(int i = 0; i < arr.length; i += 1) {
     tempArr[i] = arr[arr.length - i - 1];
   }
   for (int i = 0; i <arr.length;i++){
     arr[i] = tempArr[i];
   }
 }

```
Explanation of Fix:
> This key to patching this bug is creating a remporary array of the same size of the orginal array so that
> we are not actually changing the orginal array's values whilist looping through it. Afterwards we set the orginal array
> to the temporary array so that the changes will be displayed
> 
---
## **Part 2**
---

