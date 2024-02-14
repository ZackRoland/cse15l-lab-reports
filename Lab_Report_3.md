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
## **Part 2-Researching Commands**
The Command of Interest is the Grep Command
[link](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)
1) The first command line option is: -v
> "-v" This prints out all the lines that do not matches the pattern
```
Example 1:
[zroland@its-cseb230-25]:docsearch:518$ grep ".txt" find-results.txt > grep-results.txt
[zroland@its-cseb230-25]:docsearch:519$ wc grep-results.txt 
 1391  1391 54178 grep-results.txt
[zroland@its-cseb230-25]:docsearch:520$ grep -v ".txt" grep-results.txt  > grep-v-results.txt
[zroland@its-cseb230-25]:docsearch:521$ wc grep-v-results.txt 
0 0 0 grep-v-results.txt
```
> First store the lines that contain ".txt" into grep-results then stored the lines in grep-results 
> that do not contain ".txt" in grep-v-results and took the count of that which returns 0 lines since
> all the lines in grep-results are .txt files
```
Example 2:
[zroland@its-cseb230-25]:docsearch:522$ grep -v ".txt" find-results.txt > grep-v-results2.txt
[zroland@its-cseb230-25]:docsearch:523$ wc grep-v-results2.txt 
 11  11 291 grep-v-results2.txt
```
> This example stores all the lines in find-results.txt that aren't ".txt" files into grep-v-results2.txt
> and get the count of the lines which shows only 11 non ".txt" files

2) The second command line option is: -A n
> "-A n" Prints searched line and nlines after the result.
```
Example 1:
[zroland@its-cseb230-25]:docsearch:524$ grep -A1 "WE HAVE SOME PLANES" technical/911report/chapter-1.txt
"WE HAVE SOME PLANES"

```
>
```
Example 2:
[zroland@its-cseb230-25]:docsearch:525$ grep -A10 "WE HAVE SOME PLANES" technical/911report/chapter-1.txt
"WE HAVE SOME PLANES"

    Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millions of men and women readied themselves for work. Some made their way to the Twin Towers, the signature structures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylvania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush went for an early morning run.

    For those heading to an airport, weather conditions could not have been better for a safe and pleasant journey. Among the travelers were Mohamed Atta and Abdul Aziz al Omari, who arrived at the airport in Portland, Maine.

INSIDE THE FOUR FLIGHTS

Boarding the Flights

    Boston: American 11 and United 175. Atta and Omari boarded a 6:00 A.M. flight from Portland to Boston's Logan International Airport
```
>
3) The third command line option is: -B n
> "-B n" Prints searched line and n line before the result.
```
> Example 1:
[zroland@its-cseb230-25]:docsearch:528$ grep -B1 "WE HAVE SOME PLANES" technical/911report/chapter-1.txt

"WE HAVE SOME PLANES"
```
>
```
Example 2:
[zroland@its-cseb230-25]:docsearch:528$ grep -B1 "WE HAVE SOME PLANES" technical/911report/chapter-1.txt

"WE HAVE SOME PLANES"
```
4) The fourth command line option is: -C n
> "-C n" Prints searched line and n lines after before the result.
```
Example 1:
[zroland@its-cseb230-25]:docsearch:528$ grep -B1 "WE HAVE SOME PLANES" technical/911report/chapter-1.txt

"WE HAVE SOME PLANES"

```
>
```
Example 2:
[zroland@its-cseb230-25]:docsearch:533$ grep -C10 "WE HAVE SOME PLANES" technical/911report/chapter-1.txt



"WE HAVE SOME PLANES"

    Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millions of men and women readied themselves for work. Some made their way to the Twin Towers, the signature structures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylvania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush went for an early morning run.

    For those heading to an airport, weather conditions could not have been better for a safe and pleasant journey. Among the travelers were Mohamed Atta and Abdul Aziz al Omari, who arrived at the airport in Portland, Maine.

INSIDE THE FOUR FLIGHTS

Boarding the Flights

    Boston: American 11 and United 175. Atta and Omari boarded a 6:00 A.M. flight from Portland to Boston's Logan International Airport.
```
> 
---

