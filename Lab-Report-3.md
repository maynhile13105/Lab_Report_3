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
#### [Command `grep`](https://www.freecodecamp.org/news/grep-command-in-linux-usage-options-and-syntax-examples/#:~:text=Grep%20is%20a%20useful%20command,a%20powerful%20command%20to%20use.)

- `grep` with `-i` option

  The `-i` option allows `grep` to search and return results ignoring the cases of matching strings.

   In the example below, if we execute the command `grep "PLOS" find-results.txt`, the result will be nothing because in the file `find-results.txt` there is no line containing the exact phrase "PLOS". But if we execute the command `grep -i "PLOS" find-results.txt`, not onlt the lines containing the exact phrase "PLOS" but also all the lines containing "plos" / "Plos" / "PLos"/... were printed out.
EX1: `grep -i "PLOS" find-results.txt`
  ![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/93d1bc53-1a9e-401f-b5b1-d85c92544ff0)

EX2: `grep -i "pLoS" find-results.txt`
![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/cb26ec00-5eb8-4987-8f14-0f16af6a8afb)

  
- `grep` with `-v` option

  The `-v` option allows `grep` to search and return the files/lines that do not contain the matching string.


EX1: `grep -v "biomed" find-results.txt > grep-v-results.txt`

  ![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/c0a85d55-cda7-4bbe-b1eb-e76b07006d89)
  
  The image shows us the result of the command `grep -v "biomed" find-results.txt`. We can figure out that all lines containing the phrase "biomed" were not printed.

EX2: `grep -v "plos" find-results.txt > grep-v-results.txt`

![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/cf72ef4d-c52d-48a7-be9a-49bc9dd7cb68)

The image shows us the result of the command `grep -v "plos" find-results.txt` in a file grep-v-results.txt. We can figure out that all lines containing the phrase "plos" were not printed.
  
- `grep` with `-n` option

  The `-n` option allows `grep` to search and return the lines containing the matching string with its line number in the file.

  The image below is the result of the command `grep -n "government" find-results.txt`.
  
  ![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/e28d25ad-5478-4b65-9b1d-2ca581fd03e6)

- `grep` with `-c` option

  The `-c` option allows grep to search, count the lines containing the matching string, and then return the number of counts.
  
  Like in the file `find-results.txt`, we have 292 lines containing the phrase "government". So when the command `grep -c "government" find-results.txt" was executed, `292` was printed out as the result of the command.
  
  ![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/724c7430-7b39-450f-8eff-fd359c85e5b8)
  



