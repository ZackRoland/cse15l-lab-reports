# LAB 4: Vim

**STEP 4:**
>ssh zroland@ieng6.ucsd.edu
>This command logs me into the remote ssh where the repository will be cloned

**STEP 5:**
>git clone https://github.com/ucsd-cse15l-s23/lab7.git
>This command clones the lab7 repository into the ssh

![Image](https://i.postimg.cc/SNnQNhtK/temp-Imagea-NDcrb.avif)

**STEP 6:**
>bash test.sh
>this command runs the tests for ListExamples, it fails one as expected

![Image](https://i.postimg.cc/XYLYmm64/temp-Image-Ulr0-SJ.avif)

**STEP 7:**
>Keys Pressed:
>
>vim ListExamples.java, 44G, 1e, r2, :wq
>the "vim ListExamples.java" command pulls up the ListExamples file into a vim terminal
>44G command relocates the cursor to the line 44 where the error is located
>1e moves the cursor to the end of the 1st word which is the exact position of the error
>r2 replaces the element on the cursor with 2

![Image](https://i.postimg.cc/CxXQhLgN/temp-Imagessha-Mx.avif)

**STEP 8:**
>bash test.sh
>the bash command runs the tests for ListExamples, it passes
![Image](https://i.postimg.cc/bJcYthQ0/temp-Image2b2-Cwc.avif)

**STEP 9:**
>git add .
> 
>git commit -m “committed”
>
>git push
>
>rm -rf lab7/ (Command to delete directory)

![Image](https://i.postimg.cc/9MRxs6Sk/temp-Imagezo-D6gj.avif)
