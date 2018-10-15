# EE282 Homework2 (Due Oct 15) by Jihye Choi(94323474)
## Please design questions suitable for an upper level undergraduate course to illustrate the concepts we covered in class. Then, provide the answer key for your own questions (i.e. answer your own questions). Below, a prompt is given for the concept you are to design a question from. When given an option, try your best to choose the one that you're least familiar with so you can hone your own understanding.
1. Ask a question that requires a student to understand navigation and manipulation of directories in a filesystem. Your question should require an answer using at least the following commands/concepts: cd, ../, mkdir, rmdir  
* Create a new directory named _UCI_ in your current directory, several new subdirectory named _Bio, Computer, Math_, and then create a subdirectory _Math225_ under _Math_. Then print working directory. Next, remove _Bio_ that we made previously.

      mkdir UCI
      cd UCI
      mkdir Bio Computer Math
      cd Math 
      mkdir Math225
      pwd #print working directory will give us "/data/users/jihyec2/UCI/Math/Math225"
      cd ../ #go back to the parent directory of _Math_, which is _UCI_
      rmdir Bio

2. Ask a question that requires a student to understand the difference between accessing a column in a matrix with numeric indices versus accessing a column in a data frame with numeric indices. Your question should require an answer comparing the following: mymatrix[,1] vs. mydf[,1] vs. mydf[1] vs. mydf[[1]].
* Create a 3x6 matrix. Furthermore, obtain a spreadsheet data from the web and subsetting the dataframe like a matrix. Then explain the differences between mymatrix[,1] vs. mydf[,1] vs. mydf[1] vs. mydf[[1]].  

      mymatrix <- matrix(data = 1:18, nrow = 3, ncol = 6, byrow = TRUE)
      mymatrix[,1] #print the first column of mymatrix

      require('RCurl') #obtain data from the web
      mlbweightdfurl <- 'http://goo.gl/rih9v9'
      mlb.weight.df <- textConnection(getURL(mlbweightdfurl, followlocation  = TRUE))
      mlb.weight.df <- read.table(mlb.weight.df, header = TRUE) #read only several lines of the table. 
      mydf <- mlb.weight.df[1:3,1:6] #subsetting the dataframe (show the first three rows and six columns of the dataset)
      mydf[,1]
      mydf[1]
      mydf[[1]]
      

First of all, I create a 3x6 matrix, **mymatrix**, filled with the number from 1 to 18 in row major order. Then **mymatrix[,1]** prints the first column of the matrix, which is  **[1]  1  7 13**.
Next, I import the data from the web and subset the data, naming it as mydf. mydf[,1] and mydf[[1]] are basically same and give me the first column of the table as vectors, whereas mydf[1] shows me the first column of the table as a dataframe.


3. Ask a question that requires a student to understand how to share access to a directory and a file in that directory on a Unix/Linux filesystem from their home directory with a colleague without exposing the user's entire directory. Your question should require an answer using chmod {u,g,o}{+,-}{r,w,x} (not using octal permissions).
Hint 1: in order to view a file, all of its parent directories must be executable
Hint 2: in order to view a file, the file itself must be readable

r 040
w 200
x 100
chmod 740 name of file (executable)

admin group everyone

Ask a question that requires a student to understand how to create a simple script and make it usable by everyone, but only writeable by its creator. Your question should require an answer using chmod NNN (using octal permissions).
Hint 1: in order for a script to be executable, it must be readable and executable
Hint 2: in order for a script to be executable, all of its parent directories must be executable

* Create a simple script named _file_ under _Math225_, and make it usable by everyone but only writeable by its creator by using chmod NNN(using octal permissions). 
      mkdir jihye
      ls
      cd ./jihye
      touch file
      ls -l #check the permission status
      chmod 755 file 
      ls -l
      cd ..cd 
      chmod 755 jihye
      ls -l #
      

    


      #create a file 
      touch file 
      echo "text" > file #That method overwrites the contents of file to text.
      cat << EOF > file #contents of my file 
      test 1
      test 2 
      test 3
      EOF

      chmod +x file #make it executable

      man chomod
      chomod 744 filename 
