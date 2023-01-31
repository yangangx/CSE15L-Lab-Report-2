# Lab Report week 3

## Part 1
![Image](2-1.png)
![Image](2-2.png)
![Image](2-3.png)
![Image](2-4.png)

Which methods in your code are called?


What are the relevant arguments to those methods, and the values of any relevant fields of the class?


How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.



## Part 2

A failure-inducing input for the buggy program, as a JUnit test and any associated code
```
@Test
  public void testAverageWithoutLowest(){
    double[] input = {1, 2, 3, 3, 4};
    assertEquals(3, ArrayExamples.averageWithoutLowest(input), 0.01);
      }
```
An input that doesn’t induce a failure, as a JUnit test and any associated code
```
@Test
  public void testAverageWithoutLowest(){
    double[] input = {1};
    assertEquals(0, ArrayExamples.averageWithoutLowest(input), 0.01);
      }
```
The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)

![Image](1-3.png)

The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)
```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
       sum += num; 
    }
    return sum / (arr.length - 1);
  }
```

```
static double newAverageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      sum += num; 
    }

    sum = sum - lowest;

    return sum / (arr.length - 1);
  }
```
Briefly describe why the fix addresses the issue.
The before code calculate the sum and lowest correctly, but the main reason wihch cause the bug is the before code only calculated the sum and lowest, it didn't subtracte the lowest from the sum. The after code, I add a calculation that it does subtraction, it subtract the lowest from the sum. For example above, the array is 1, 2, 3, 3, 4, the expect value is 3, but the actual value is 3.25. it just because the before code didn't subtract the lowest value 1 from the sum.

## Part 3
In a couple of sentences, describe something you learned from lab in week 2 or 3 that you didn’t know before.

I learned how to clone from github, and I use vscode to clone from github to my computer through the git clone command. I learned what makes up a URL in the section How to distinguish URLs in a URL Domain path Query and Anchor. I also learned about the commands to build and run the server. How to use JUnit for debugging. These are things I didn't know before.




