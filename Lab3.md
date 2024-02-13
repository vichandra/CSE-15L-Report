

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


The third way of using grep is with -n: grep -n "pattern" file.txt is an example, where we are trying to find the number of instances of "pattern" in the file `file.txt`
```
grep -n "water" water_fees.txt

5:Alpaugh water fees may triple
10:Alpaugh residents may see their water fees triple to avoid
13:District 1 meeting. The district, which provides water service to
16:water.
18:Alpaugh Irrigation District, which supplies water to farmers in the
19:area, ends July 1. And Alpaugh Irrigation, which provides water,
21:Works, is scaling back its role. The district will sell only water
25:fast enough to meet the rising cost of delivering water, amassed an
43:The farmworker thought the water was getting turned off today,
```

In this case, we were within docsearch/technical/government/Media, and wanted to find the number of instances of "water" within the file water_fees.txt. The output resulted the lines where "water" appeared in the text


if we wanted to search instances of "water" within a directory, the command is similar: `grep -nr "water" directory/` 
```
virajchandra@Virajs-MacBook-Pro technical % grep -nr "water" 911report/

911report//chapter-13.5.txt:3168:            7. For the Goldwater-Nichols Act, see Pub. L. No. 99-433, 100 Stat. 992 (1986). For a
911report//chapter-13.5.txt:3170:                Staff: The Goldwater-Nichols Act of 1986 (Greenwood,1999); James Locher, Victory on
911report//chapter-13.5.txt:3171:                the Potomac: The Goldwater-Nichols Act Unifies the Pentagon (Texas A&M Univ.
911report//chapter-13.1.txt:157:            Recalling the Goldwater-Nichols legislation of 1986, Secretary Rumsfeld reminded us
911report//chapter-13.1.txt:350:                By contrast, in organizing national defense, the Goldwater- Nichols
911report//chapter-13.1.txt:355:                    like the commanding general of the Central Command (CENTCOM). The Goldwater-
911report//chapter-13.3.txt:925:                Goldwater-Nichols Act of 1986 (Greenwood, 1999).
911report//chapter-3.txt:1072:            The first was the passage by Congress in 1986 of the Goldwater-Nichols Act, which,
911report//chapter-3.txt:1080:                presented to the president. The Goldwater-Nichols example is seen by some as having
911report//chapter-3.txt:1108:                the armed forces. It also contributed to the later Goldwater-Nichols reforms.
911report//chapter-3.txt:1329:                critical infrastructures, our power systems, water supplies, police, fire, and
911report//chapter-3.txt:2275:                complained to us that the original plan "had been watered down to the point that
911report//chapter-5.txt:153:                Salaam marked a watershed in the evolution of the 9/11 plot. KSM claims these
911report//chapter-5.txt:272:                foreign ships plying the waters along the southwest coast of Yemen.
911report//chapter-9.txt:481:                whether water for firefighting would be available on the upper floors. They also did
911report//chapter-11.txt:517:                with the Goldwater-Nichols reforms, Shelton had been the only member of the JCS to
911report//chapter-11.txt:681:                many and that, at the time, it was "considered interesting, but not heavy water
```


for our final example of using grep, we can use `-w`.


for files, here is how the command looks if wanted to search for "word" within file.txt: `grep -w` "word" `file.txt`. This command searches for the word "water" within all files in the "911report" directory and its subdirectories, displaying the line number along with each matching line.

```
virajchandra@Virajs-MacBook-Pro 911report % grep -w "chair" preface.txt

            Thomas H. Kean, chair
            Lee H. Hamilton, vice chair
```
This command searches for the whole word "word" in file.txt, rather than matching it as part of a larger word.

for directories, we use -wr so we can check through all files and subdirectories within the directory we are looking at to see if the character,word, or pattern exists, and where and how manytimes.
`grep -wr`
```
virajchandra@Virajs-MacBook-Pro technical % grep -wr "God" 911report/

911report//chapter-13.3.txt:                their rooftops and chanted with one voice,'God is great.'This open defiance of the
911report//chapter-3.txt:                fight against God's enemies. An FBI informant learned of a plan to bomb major New
911report//chapter-3.txt:                grabbing his beard and saying emotionally, "By Allah, by God, the Americans will
911report//chapter-2.txt:                declared war against God and his messenger, they called for the murder of any
911report//chapter-2.txt:            Islam Islam (a word that literally means "surrender to the will of God") arose in
911report//chapter-2.txt:                from the one and only God, the God of Abraham and of Jesus. These revelations,
911report//chapter-2.txt:                from Abraham through Jesus, complete God's message to humanity. The Hadith, which
911report//chapter-2.txt:                legislation, only prove these rulers to be false Muslims usurping God's authority
911report//chapter-2.txt:                as a struggle between God and Satan. All Muslims-as he defined them-therefore must
911report//chapter-1.txt:    At 8:44, Gonzalez reported losing phone contact with Ong. About this same time Sweeney reported to Woodward, "Something is wrong. We are in a rapid descent . . . we are all over the place." Woodward asked Sweeney to look out the window to see if she could determine where they were. Sweeney responded:"We are flying low. We are flying very, very low. We are flying way too low." Seconds later she said,"Oh my God we are way too low." The phone call ended.
911report//chapter-1.txt:    At 9:00, Lee Hanson received a second call from his son Peter: It's getting bad, Dad-A stewardess was stabbed-They seem to have knives and Mace-They said they have a bomb-It's getting very bad on the plane-Passengers are throwing up and getting sick-The plane is making jerky movements-I don't think the pilot is flying the plane-I think we are going down-I think they intend to go to Chicago or someplace and fly into a building-Don't worry, Dad- If it happens, it'll be very fast-My God, my God.
911report//chapter-1.txt:    FAA Headquarters: Oh, God, I don't know.
911report//chapter-10.txt:                the sensibilities of Muslims who associate the power of infinite justice with God
```
