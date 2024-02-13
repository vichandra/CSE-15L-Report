

## Part 1 - Bugs

the first code block is the issue found in the tester (failure inducing output) caused by the faulty method. 
The second block of code is  another tester that does not cause any failure inducing output the method itself. 

```
@Test
  public void testR2(){
    int [] input = {1,2,3,4,5,6};
    input = ArrayExamples.reversed(input);
    assertArrayEquals(new int[]{6,5,4,3,2,1},input);
  }
```
```
@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
```

the following is a test that would not indicate an issue with the code:
```
@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}



// Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

### Here are the symptoms of the JUNIT tests

![img](https://cdn.discordapp.com/attachments/1039377931253854269/1207026528626671746/Screenshot_2024-02-13_at_10.07.39_AM.png?ex=65de260d&is=65cbb10d&hm=45340d002ea79f3f09a2c7e4ae273d1f41b7e775104899cc27430640634e5a45&)



