# Large-File-Processing-with-Multi-threading
# Large File Processing with Multi-threading in Java

## Project Overview
This project demonstrates how to process large CSV files efficiently using multi-threading in Java.

Instead of processing the file sequentially, the program divides the file into smaller chunks and processes them in parallel using multiple threads.

## Project Idea
When dealing with large files, processing them using a single thread can be slow.  
This project solves the problem by using multi-threading to process different parts of the file simultaneously.

## Workflow

1. Read the file using BufferedReader.
2. Split the file into chunks.
3. Assign each chunk to a thread.
4. Use ExecutorService to manage threads.
5. Process chunks in parallel.
6. Combine the results.

## Technologies Used
- Java
- Multi-threading
- ExecutorService
- BufferedReader
- File Handling

## Expected Result
The program processes large files faster by using parallel processing with multiple threads.
