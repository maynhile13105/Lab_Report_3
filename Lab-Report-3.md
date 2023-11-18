# Lab Report 3

### ***Part 1 - Bugs***

- ***A failure-inducing input for the buggy program, as a JUnit test and any associated code***

  ```
  @Test 
	public void testReverseInPlace() {
    int[] input1 = { 3,5,6,8 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 8,6,5,3 }, input1);
	}
  ```

- ***An input that doesn’t induce a failure, as a JUnit test and any associated code***

  ```
  @Test 
	public void testReverseInPlace1() {
    int[] input1 = { 5 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 5 }, input1);
	}
  ```

- ***The symptom, as the output of running the tests***

 
![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/ef2e25bc-18a3-4925-9dc0-c04406d525e3)

 
- ***The bug, as the before-and-after code change required to fix it***
    - The bug before fixing:
      ```
      static void reverseInPlace(int[] arr)
      {
        for(int i = 0; i < arr.length; i += 1) {
          arr[i] = arr[arr.length - i - 1];
        }
      }
      ```
    - The bug is fixed:
      ```
      static void reverseInPlace(int[] arr)
      {
        for(int i = 0; i < arr.length/2; i += 1)
        {
          int temp =arr[i];
          arr[i] = arr[arr.length - i - 1];
          arr[arr.length - i - 1]=temp;
        }
      }
      ```

      The expected output of the given algorithm is that only the first half of the array changes its value to the second half of the array. The problem with this algorithm is that while we swap, we accidentally lose the original value of the first half of the array. So, we can see that we need to store the original value of the first half of the array before converting it to the second half of the array.
Therefore, to fix this bug, I created a variable `temp` to temporarily store the original value of `arr[i]` before converting it to the value of `arr[arr.length - i - 1]`. After that, I changed the value of `arr[i]` to `arr[arr.length - i - 1]` and then I assign the value of `temp` to `arr[arr.length - i - 1]`. As a result, I swapped the values of `arr[i]` and `arr[arr.length - i - 1]` with each other. Also, in each iteration i, I swap the value of the front half of the array (`arr[i]`) and the second half of the array (`arr[arr.length - i-1`) at the same time. So my loop only needs to run from 0 to the end of the first half of the array (`array.length/2`)
### ***Part 2 - Researching Commands***


- *`grep` with `-i` option*

#### Source: [Grep Command in Linux – Usage, Options, and Syntax Examples](https://www.freecodecamp.org/news/grep-command-in-linux-usage-options-and-syntax-examples/#:~:text=Grep%20is%20a%20useful%20command,a%20powerful%20command%20to%20use.)

The `-i` option allows `grep` to search and return results ignoring the cases of matching strings.

In the example below, if we execute the command `grep "PLOS" find-results.txt`, the result will be nothing because in the file `find-results.txt` there is no line containing the exact phrase "PLOS". But if we execute the command `grep -i "PLOS" find-results.txt`, not onlt the lines containing the exact phrase "PLOS" but also all the lines containing "plos" / "Plos" / "PLos"/... were printed out.

For examples:
	
 	`grep -i "PLOS" find-results.txt`

![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/74e09274-2966-4b2e-bd14-cf16f1b2fd4e)
  
	`grep -i "pLoS" find-results.txt`

![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/311ca02e-3e59-4275-bb88-ee3fe383c699)

  
- **`grep` with `-v` option**

#### Source: [Grep Command in Linux – Usage, Options, and Syntax Examples](https://www.freecodecamp.org/news/grep-command-in-linux-usage-options-and-syntax-examples/#:~:text=Grep%20is%20a%20useful%20command,a%20powerful%20command%20to%20use.)

The `-v` option allows `grep` to search and return the files/lines that do not contain the matching string.

For examples: 

	`grep -v "biomed" find-results.txt > grep-v-results.txt`

 ![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/e7a95f73-10ee-4b10-9cdb-cdb4ec952795)
 
 The image shows us the result of the command `grep -v "biomed" find-results.txt`. We can figure out that all lines containing the phrase "biomed" were not printed.
 
	`grep -v "report" find-results.txt > grep-v-results.txt`

 ![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/d128d9ad-3cbf-4dcc-b2fc-a6a6acdd99a8)
 
 The image shows us the result of the command `grep -v "report" find-results.txt` in a file grep-v-results.txt. We can figure out that all lines containing the phrase "report" were not printed.
  
- **`grep` with `-n` option**

  #### Source: [Grep Command in Linux – Usage, Options, and Syntax Examples](https://www.freecodecamp.org/news/grep-command-in-linux-usage-options-and-syntax-examples/#:~:text=Grep%20is%20a%20useful%20command,a%20powerful%20command%20to%20use.)

  The `-n` option allows `grep` to search and return the lines containing the matching string with its line number in the file.

  For examples:
  
  	`grep -n "government" find-results.txt`.

  ![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/61c72442-1e0e-4970-911a-717b7f0875de)

  	`grep -n "chapter-1" find-results.txt`

  ![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/897559cc-68aa-45bb-a1ca-d7894e802f1c)


- **`grep` with `-c` option**

  #### Source: [Grep Command in Linux – Usage, Options, and Syntax Examples](https://www.freecodecamp.org/news/grep-command-in-linux-usage-options-and-syntax-examples/#:~:text=Grep%20is%20a%20useful%20command,a%20powerful%20command%20to%20use.)

  The `-c` option allows grep to search, count the lines containing the matching string, and then just return the number of counts.
  For examples:

  	`grep -c "government" find-results.txt`

  ![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/724c7430-7b39-450f-8eff-fd359c85e5b8)

  	`grep -c "Gen_Account_Office" find-results.txt`
 
  ![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/26d5a9ec-b913-4d38-a374-80e73daa2c16)




