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
	public void testReverseInPlace() {
    int[] input1 = { 5 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 5 }, input1);
	}
  ```

- ***The symptom, as the output of running the tests***

  - The output of running the first test:

![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/ef2e25bc-18a3-4925-9dc0-c04406d525e3)

 
  - The output of running the second test:

![image](https://github.com/maynhile13105/Lab_Report_3/assets/146885739/b1b01448-d119-4f31-81a3-ac6d42341206)
    

- ***The bug, as the before-and-after code change required to fix it***
    - The bug before fixing:
      ```
      static void reverseInPlace(int[] arr)
      {
        for(int i = 0; i < arr.length; i += 1) {
          arr[i] = arr[arr.length - i - 1];
        }
      }

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
Therefore, to fix this bug, I created a variable `temp` to temporarily store the original value of `arr[i]` before converting it to the value of `arr[arr.length - i - 1]`. After that, I change the value of `arr[i]` to `arr[arr.length - i - 1]` and then I assign the value of `temp` to `arr[arr.length - i - 1]`. As a result, I swapped the values of `arr[i]` and `arr[arr.length - i - 1]` with each other. Also, because in each iteration i, I swap the value of the front half of the array (`arr[i]`) and the second half of the array (`arr[arr.length - i-1`) at the same time. So my loop only needs to run from 0 to the end of the first half of the array (`array.length/2`)
### ***Part 2 - Researching Commands***
#### [Command `grep`](https://www.freecodecamp.org/news/grep-command-in-linux-usage-options-and-syntax-examples/#:~:text=Grep%20is%20a%20useful%20command,a%20powerful%20command%20to%20use.)

- `grep` with `-i`
  
- `grep` with `-v`
- `grep` with `-r`
- `grep` with `-w`


