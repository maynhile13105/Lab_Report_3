***#LAB Report 4***
**Step 4: Log into *ieng6***

Key pressed: `ssh cs15lfa23lp@ieng6.ucsd.edu<Enter>`

Because I authorize my computer to access ssh, it automatically logs in without asking for a password.

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/4a8dad6d-ce41-46ca-9e64-655e66343bda)

**Step 5: Clone the fork of the repository from the GitHub account using `ssh`***

Keys pressed: `git clone <Ctrl+V><Enter>`

Actual command: `git clone git@github.com:maynhile13105/lab7.git`

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/720cb7a4-5c47-4299-9542-f992e87eec61)

Before git clone, I copied a ssh URL. So, press `<Ctrl+V>` to paste the URL to the terminal. 

The pressed keys build and make the command `git clone git@github.com:maynhile13105/lab7.git` execute.


**Step 6: Run the test, demonstrating that they fail***

Key pressed: `cd lab7<Enter>bash test.sh<Enter>`

Actual command:

```
cd lab7

bash test.sh
```

First, change the directory to lab7. Then run the test by using the command `bash test.sh`
![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/65fb8bba-9e09-4929-993c-e043d29b6d43)

**Step 7: Edit the code file to fix the failing test***

Key pressed: `vim L<Tab>.<Tab><Enter>` 

- `L<Tab>.<Tab>` becomes `ListExamples.java`. Because `L<Tab>` becomes `ListExamples`, then assign it with the `.<Tab>` means turns it into `ListExamples.<Tab>`, which becomes `ListExamples.java`. 
So, the actual command `vim ListExamples.java` executes and it opens the file `ListExamples.java` via `vim`. I used `<Tab>` to quickly get the file's name. However, because there are two files starting with `L` and containing `ListExamples`, so first `<Tab>` just can help us quickly get `ListExamples`. The file we need to open has `.` following, which is different from the other file followed by `T`. So I press `.` following the first `<Tab>`. The second `<Tab>` is used to get `java` quickly. 

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/3d3c6c11-5f6a-4ebf-aaad-3d32d24488ee)

Key pressed: `:44s/1/2<Enter>` 
- Then, because we have to change `index1` into `index2` in the line 44 of the file, so I have pressed `:44s/1/2<Enter>`. In `vim`, this means the index goes to line 44, then replace the first number `1` with the number `2`.
  
![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/f9e19c43-0e3e-4654-b6a8-33abefd9bd2a)

Key pressed: `:wq<Enter>`

- Finally, `:wq` means save all the changes we made and then exit `vim` to get back to the terminal.

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/077cab7c-c215-44fa-ad3f-1a58509c39cd)

  
**Step 8: Run the test, demonstrating that they now succeed***

Key pressed: `<up><up><Enter>`

The command `bash test.sh` is 2 up in the search history, so I pressed up key twice to access it quickly.

The key `<Enter>` is for the command executes. 

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/b84f93bb-ad46-4b4a-80da-1923f499218f)


**Step 9: Commit and push the resulting change to the GitHub account***

Key pressed: `git add L<Tab>.j<Tab>`

Similar to the case using `<Tab>` above, `L<Tab>` is for quick access to `ListExamples`. Then, instead of using `.<Tab>`, I pressed `.j<Tab>` because there are two files whose name contains `ListExamples.` (`ListExamples.java` and `ListExamples.class`). 

Actual command: `git add ListExamples.java`

The `git add` command adds changes to the staging area and makes sure that ListExamples.java has changes 
and is ready to be committed.

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/8a1449c0-79ae-4f9c-a882-3b2218d59ff7)

Key pressed: `git commit<Enter>` to commit the file. When the command executes, it opens a file where we leave messages while committing via `vim`

Key pressed: `i` to access the insert mode, then enter the messages, in this example is `update`.

Key pressed: `<Esc` to exit the insert mode and get back to normal mode. 

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/58b5e757-53e4-4ffa-a33a-0a80808908ad)

Key pressed: `:wq` to save the changes and go back to the terminal. 

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/9c10215d-1e15-4f38-b0a0-ca122a7cad32)

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/5452650d-d7be-4117-af40-19fd3f5fa0f6)

Key pressed: `git push`

The `git push` command is used to push the file we just committed and the messages to the fork in the Github account. 
![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/a20dff62-24ba-46c9-ac29-95b08e02d436)
