# Lab Report 5

## Example of Student Question on EdStem:

### Student:

### I was working on creating a method that can take any array array and reverse the order of the elements. I am not sure what happened but I am getting the wrong expected values. I am not sure what is wrong with my logic but I would like and suggestions or guidance on what the issue is and what I can change. I pasted my code below:
```
public class ArrayExamples {

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }

  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }

  // Averages the numbers in the array (takes the mean), but leaves out the
  // lowest number when calculating. Returns 0 if there are no elements or just
  // 1 element in the array
  static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
}
```
### Student: Here is my testing class as well as the failure output I recieved from the terminal:
### I believe it may have something to do with the line ` arr[i] = newArray[arr.length - i - 1]; ` but I am not sure.
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
        @Test
        public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
        }


  @Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
 @Test
  public void testvalidReversed() {
    int[] input1 = {1,2,3,4 };
    assertArrayEquals(new int[]{4,3,2,1 }, ArrayExamples.reversed(input1));
  }
}
```

![img](https://cdn.discordapp.com/attachments/974137838180380672/1216163120867835975/Screenshot_2024-03-09_at_3.12.46_PM.png?ex=65ff632b&is=65ecee2b&hm=929385c21eba2239a6e0d782943a98ef4894f4809339bf131b8cda88cd29e0e7&)

## TA Response:

Hi, you're in the right direction. it seems your tester is expecting a value that was never initially there in your array setup. Try thinking about how this method goes about reversing this array and what happens to the data in the argument array. It may help to notice how it is different from ReverseInPlace(), because they're implementation can explain why you are expecting a 0 as the first element in your array, even if it was never part of your array. (hint: you are using two arrays, how does that affect your implemetnation?)




## Student Response:
I think I managed to figure out the line of code that was causing me trouble, which happened to be what I thought it was. I changed `arr[i] = newArray[arr.length - i - 1];` to `arr[i] = newArray[arr.length - i - 1];`
This made sense to me since we didnt intialize newArray yet, so the values would obviously be 0. I changed the line of code so the final method looks like this:
```
 static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i]= arr[arr.length - i - 1];
    }
    return newArray;
  }
```
