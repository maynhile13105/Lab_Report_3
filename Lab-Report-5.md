# Lab Report 5

### Part 1

- ***The original post from a student***

  ![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/9a866b26-a21b-4577-8463-79c67bf5ab61)

Hi instructors, 

While I was trying to run the JUnit tests, I encountered an issue. Based on my understanding from the messages, something around line 42 of the ListExamples.java file caused my test on the `merge` function from ListExamplesTests.java to time out after 500 milliseconds. I tried to figure the bug out but could not. Can you help me with what is happening?

The failure-inducing input:

```
@Test(timeout = 500)
        public void testMerge2() {
		        List<String> l1 = new ArrayList<String>(Arrays.asList("a", "b", "c"));
		        List<String> l2 = new ArrayList<String>(Arrays.asList("c", "d", "e"));
		        assertArrayEquals(new String[]{ "a", "b", "c", "c", "d", "e" }, ListExamples.merge(l1, l2).toArray());
         }
```

- ***The response from a TA***

  Hello,
  You are right. Using JUnit testing to identify the location of bugs is important. It helps us minimize the time it takes to fix bugs. With this time-out issue, I recommend you check your logic. You can use `jdb` to debug and stop at the desired position as the professor mentioned in the course. You can use `step` to run to the next line.


- Student's implementation

 ![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/c7bb6fb0-e862-497e-80f7-d5472a9d6ace)

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/88b7aca6-eed4-4117-9916-b8e73c1235d3)

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/16139fd4-185a-4508-b82d-c740dc79fbd6)

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/178a86b8-f13e-4e96-ba6a-0615fbf937ee)




- Screenshots
