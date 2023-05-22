ITCS 6114 : Algorithms and Data Structures


Name : Jaswanth Yadla
Student ID: 801275432
Sec : 002
Email Id : jyadla@uncc.edu


Program Design :
The Algorithm implemented is LZW.
* It includes Compressing/Encoding and Decompressing/Decoding of the files.


Encoding 
*  In the Encoding phase, this algorithm reads an input sequence of symbols, combines them into strings and represents these strings with integer values. 
* The Data Structure used is HashMap, Initially we store the ASCII values of range from 0-255 in hashmap. Here String is stored as keys and Integer is stored as value.
* The input to encoder.java file is an ASCII text file, which is specified in the Command line followed by bit length and the output file is stored as .lzw extension.  
*  BufferedReader class is used to read the characters from the input text file. It checks whether the key is present in the hashmap or not, if not present, it outputs the previous string to the output file using the BufferedWriter class with write() method and then stores the new string in hashmap and sets the new string to the previous string. If the key is present then it concatenates the previous string and new string to the previous string.
* This loop exits when the file reaches the end. Then it finally writes the string to the output file. Encoded Output is saved as 2 bytes in 16 bit format.


Decoding 
* In the Decoding Phase, the input to this algorithm is the output from the encoder phase followed by the bit length. The output file is stored as .txt format.
* Table Size is computed as 2^bitlength, whenever the algorithm has to add a key,value pair it checks whether current table size < Maximum Table Size.
* HashMap Data Structure is used to store the first 256 ASCII extended characters. Both the phases construct the same dictionary. Here Integers are stored as Keys and String is stored as Values.
* InputStreamReader class is used to convert bytes to characters in the specified character set format. This class is wrapped in the BufferedReader class to achieve better efficiency in reading the file. Initially we decode the first character and write that to an output file.
* Then the data in the file is read integer by integer and checks whether it is present in the hashmap or not, if not present ,the previous string is concatenated with the first character of the previous string and stores the concatenated string in a new string. The value of this new string is written to the output file. If it is present in the hashmap, then the corresponding value is written to the output file.
* After writing to the output file, the previous string is concatenated with the first character of the new string which is then stored in the hashmap and now the new string is stored as string.
* OutputStreamWriter is used to write to output files in the “UTF-8” character set. 


Programming Language and Version
The Programming Language used is JAVA and the version used is 1.8.0_251.


Running the Program 
1. In the terminal, we have to open the directory the file is present.
2. For encoding, type
 javac encoder.java 
 java encoder <input file name.txt> <bit length>.
3. For decoding, type
javac Decoder.java 
java Decoder <input file name.lzw> <bit length>.


         
What works and what doesn't work 
The program gives the correct output for the examples and also can handle empty text files. 
But if the input size is so large that, if it requires more size than the maximum table size, then those files cannot be handled as the bit length is prefixed.