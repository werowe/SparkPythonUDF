This Jupyter notebook demonstrates how to use PySpark to create, manipulate, and transform a DataFrame and its underlying RDD, including converting string values to an integer representation using custom logic.

---

### Step-by-Step Explanation

#### 1. **PySpark Context and DataFrame Creation**
- Imports PySpark libraries and creates a SparkContext and SQLContext.
- Defines a schema with three columns: `sales` (float), `employee` (string), `ID` (integer).
- Constructs a single-row DataFrame with sample data.

#### 2. **Custom UDF for String to Integer Encoding**
- Defines a Python function, `toInt`, that takes a string and converts each character into its ASCII code, concatenates these codes into a single string, and returns the result as an integer.
- Registers this function as a Spark UDF (`colsInt`) for use in SQL/DataFrame transformations.

#### 3. **Applying UDF to DataFrame**
- Adds a new column `semployee` to the DataFrame where each `employee` value is transformed to the integer encoding via the UDF.

#### 4. **Displaying Results**
- Uses `show()` to print out the DataFrame with the new column, illustrating the transformation.

#### 5. **Using SQL with Registered DataFrame**
- Registers the original DataFrame as a temporary SQL table.
- Runs a SQL query to select all columns and the integer-encoded employee via the UDF, storing the result in a new DataFrame and displaying it.

#### 6. **RDD Conversion and Map Transformation**
- Converts the DataFrame into an RDD (Resilient Distributed Dataset).
- Defines a function `toIntEmployee` that applies the same string-to-integer conversion logic for RDD rows, building a new Row object with the encoded value.
- Applies this function with `map` to each row of the RDD.

#### 7. **Inspecting the Final RDD**
- Collects and prints all results from the RDD, displaying the custom-encoded employee values
