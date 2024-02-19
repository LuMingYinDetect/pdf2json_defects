Affected Version:
pdf2json 0.71 b671b647a7e487b021744f330b8dd2d6ccfa8103

Vulnerability Description:
The vulnerability is a memory leak bug located at line 1368 of the file /pdf2json/src/ImgOutputDev.cc. This vulnerability could potentially be exploited maliciously to cause resource exhaustion and denial of service attacks.

pdf2json download address:
https://github.com/flexpaper/pdf2json.git

Defect details:

1.In the file ImgOutputDev.cc located in /pdf2json/src/, a pointer named 'file' is defined at line 1355, and a block of dynamic memory is allocated for this pointer using the new operator. When the if statement at line 1356 evaluates to false, due to the lack of a break statement in the case statement at line 1352, the program executes the code in the default branch at line 1367. It returns a dynamically allocated memory created by the new operator at line 1368. During this process, the memory pointed to by 'file' is neither used nor freed, resulting in a memory leak defect, as illustrated in the following figure:

![image](https://github.com/LuMingYinDetect/pdf2json_defects/blob/main/pdf2json_1.png)
