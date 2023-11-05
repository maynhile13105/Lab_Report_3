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
### ***Part 2 - Researching Commands***
