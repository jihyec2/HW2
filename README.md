# EE282 Homework2 (Due Oct 15) by Jihye Choi(94323474)
## Please design questions suitable for an upper level undergraduate course to illustrate the concepts we covered in class. Then, provide the answer key for your own questions (i.e. answer your own questions). Below, a prompt is given for the concept you are to design a question from. When given an option, try your best to choose the one that you're least familiar with so you can hone your own understanding.
1. Ask a question that requires a student to understand navigation and manipulation of directories in a filesystem. Your question should require an answer using at least the following commands/concepts: cd, ../, mkdir, rmdir  
* Create a new directory named _UCI_ in your current directory, several new subdirectory named _Bio, Computer, Math_, and then create a subdirectory _Math225_ under _Math_. Then print working directory. Next, remove _Bio_ that we made previously.

      mkdir UCI #make a new directory called UCI
      cd UCI #change the directory to UCI
      mkdir Bio Computer Math #make new subdirectories
      cd Math #change the directory
      mkdir Math225 #make a new subdirectory 
      pwd #print working directory (it will give us "/data/users/jihyec2/UCI/Math/Math225")
      cd ../ #go back to the parent directory of Math, which is UCI
      rmdir Bio #remove the directory, Bio

### Question 1 Comments:
This was very well done! Great job.

2. Ask a question that requires a student to understand the difference between accessing a column in a matrix with numeric indices versus accessing a column in a data frame with numeric indices. Your question should require an answer comparing the following: mymatrix[,1] vs. mydf[,1] vs. mydf[1] vs. mydf[[1]].
* Create a 3x6 matrix. Furthermore, obtain a spreadsheet data from the web and subsetting the dataframe like a matrix. Then explain the differences between mymatrix[,1] vs. mydf[,1] vs. mydf[1] vs. mydf[[1]].  

      mymatrix <- matrix(data = 1:18, nrow = 3, ncol = 6, byrow = TRUE)
      mymatrix[,1] #print the first column of mymatrix

      require('RCurl') #obtain data from the web
      mlbweightdfurl <- 'http://goo.gl/rih9v9'
      mlb.weight.df <- textConnection(getURL(mlbweightdfurl, followlocation  = TRUE))
      mlb.weight.df <- read.table(mlb.weight.df, header = TRUE) #read only several lines of the table. 
      mydf <- mlb.weight.df[1:3,1:6] #subsetting the dataframe (show the first three rows and six columns of table)
      mydf[,1]
      mydf[1]
      mydf[[1]]
      

First of all, I create a 3x6 matrix, **mymatrix**, filled with the number from 1 to 18 in row major order. Then **mymatrix[,1]** prints the first column of the matrix, which is  **[1]  1  7 13**.
Next, I import the data from the web and subset the data, naming it as **mydf. mydf[,1] and mydf[[1]]** are basically the same and give me the first column of the table as vectors. However, **mydf[1]** shows me the first column of the table as a dataframe.

### Question 2 Comments:

Good job. Also worth noting is that indexing using [,1] is the only option available for accessing columns in matrices that we discussed.

3. Ask a question that requires a student to understand how to create a simple script and make it usable by everyone, but only writeable by its creator. Your question should require an answer using chmod NNN (using octal permissions).  
Hint 1: in order for a script to be executable, it must be readable and executable  
Hint 2: in order for a script to be executable, all of its parent directories must be executable

* Create a simple script and make it usable(readable and executable) by everyone(including group members) but only writeable by its creator by using chmod NNN(using octal permissions). 

      mkdir jihye #make directory as jihye
      ls #list the contents of my current directory 
      cd ./jihye #change directory to jihye
      touch file #create script called file
      ls -l #list the contents of jihye and check the permission status of its contents
      chmod 755 file #change the permission of file
      ls -l #confirm that permission is changed by showing the list
      cd .. #go back to the parent directory of jihye
      chmod 755 jihye #change the permission of jihye
      ls -l #confirm that permission is changed by showing the list
      
### Question 3 Comments:
This was also very well done! Great job.
