# 💧 Water Access Analysis using Multi-threading in Java

## 📌 **Project Overview**

Water Access Analysis is a Java-based project that analyzes large datasets related to water availability and accessibility in different regions. The project processes a large CSV file containing information about population, water sources, distance to water, and water access percentage.

To improve performance when handling large datasets, the project uses **multi-threading in Java**. Instead of processing the entire dataset sequentially with a single thread, the program divides the data into smaller chunks and processes them in parallel using multiple threads.

This method significantly reduces processing time and demonstrates the use of **parallel computing for real-world data analysis**.

---

## 💡 **Project Idea**

The main idea of this project is to analyze water accessibility data efficiently using **parallel processing**.

Large datasets can take a long time to process using a single thread. To solve this problem, the program splits the dataset into smaller parts and assigns each part to a different thread. Each thread processes its chunk simultaneously, which improves speed and efficiency.

---

## ⚙️ **Project Workflow**

1. Read the large CSV dataset using **BufferedReader**.
2. Split the dataset into smaller chunks.
3. Assign each chunk to a separate **thread**.
4. Use **ExecutorService** to manage and run threads.
5. Process the data in **parallel**.
6. Combine and analyze the final results.

---

## 🛠 **Technologies Used**

- Java  
- Multi-threading  
- ExecutorService  
- BufferedReader  
- CSV File Processing  

