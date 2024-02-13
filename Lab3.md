

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




## Part 2 - Researching Commands: Grep


The first way we will use grep is with the key word `-o`. When utilized with grep, prints only the matching part of each line that contains the specified pattern. it isolates and outputs the specific matched substrings or patterns.

 ```
virajchandra@Virajs-MacBook-Pro 911report % grep -o "care" chapter-1.txt
care
care

```

In the context above, using grep -o to find a pattern in a file will print out all occurences of care in the file, excluding the the other words in the line that it was found in. This is an efficient way to check the occurences of a word, character, or phrase that can save time.

We can use `grep` and `-o` with another key word `r` to help us find a character,word, or pattern in the specified directory and its subdirectories and print only the matching part of each line.


```
virajchandra@Virajs-MacBook-Pro technical % grep -ro "rubble" 911report/
911report//chapter-13.5.txt:rubble
```

In this case, using `grep` with both `r` and `o` allows searching the word "rubble" within several number of files within the sub directory of `911report`, and provided 1 instance in the file `chapter-13.5.txt` where the word "rubble" was found


The second way of using grep is with the key word `-E`. You can search for lines containing  2 key words as arguments. for example either `"pattern1"` or `"pattern2"`. This is a way to  implement OR logic in a search.


```
virajchandra@Virajs-MacBook-Pro biomed % grep -E "death|molecule" 1471-2202-3-5.txt 
        appears that the same molecules previously identified as

```
 In the example above the command searches for a "death or "molecule" within files in the biomed/ and print only the matching part of each line.




When looking through a directory, the implementation of `grep -E` is relativley similar. Instead of just using `-E`, we use `-Er`

```
grep -Er "iphone|chromium" biomed/
biomed//1471-2334-3-9.txt:        evaluated. Only the copper and chromium PcS were able to
biomed//1477-7827-1-6.txt:          solution (0.025% chromium potassium sulfate, 0.25%
biomed//1471-2172-3-9.txt:        chromium release cytotoxic assay was performed by the
biomed//1471-2172-3-9.txt:        the corresponding increase in the chromium release values
biomed//1471-2172-3-9.txt:        corresponding increase in the chromium release values is
```

With this command, grep searches for lines containing either `"iphone"` or `"chromium"` within the files in the specified directory `biomed/`.

