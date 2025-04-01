# Python YAML Use Case.

### What is YAML?
YAML (YAML Ain't Markup Language) is a human-readable data format used for configuration files and data serialization. It is widely used in programming due to its simplicity and ease of use. YAML uses indentation-based structure similar to Python, making it more readable compared to JSON or XML. 

#### Key Features of YAML:
- Uses indentation for structure instead of brackets or tags.
- Supports key-value pairs, lists, and nested structures.
- Commonly used in configuration files (e.g., Kubernetes, Ansible, Docker Compose).
- Allows comments using `#`.

## Step-by-Step Guide -

### Step 1: Install Required Packages
To handle YAML files in Python, you will need the PyYAML library. If you don't have it installed, you can install it using pip. Open your terminal and run:

- pip install pyyaml

![img](https://github.com/Panchikagupta05/Yml-file-Usecase/blob/91c8303d9f98d105dd0e65fb6d9f045ae39eec6c/Requirement%20Install.png)

### Step 2: Create the YAML File
Create a YAML file named `students.yaml`. This file will contain information about students, including their names, ages, majors, and GPAs.

#### Example `students.yaml` file:

```
students:
  - name: Alice
    age: 21
    major: Computer Science
    gpa: 3.8
  - name: Bob
    age: 22
    major: Mathematics
    gpa: 3.5
  - name: Charlie
    age: 20
    major: Physics
    gpa: 3.9
  - name: David
    age: 23
    major: Chemistry
    gpa: 3.2
  - name: Eva
    age: 21
    major: Computer Science
    gpa: 3.7
```

### Step 3: Write the Python Application
Create a new Python file named `app.py`. This script will read the data from the YAML file, allow users to view all students, and filter students by GPA.

#### `app.py` Code:

```
import yaml

def load_data(file_path):
    """
    Load data from a YAML file.
    :param file_path: Path to the YAML file.
    :return: Data loaded from the YAML file.
    """
    with open(file_path, 'r') as file:
        data = yaml.safe_load(file)  # Load the data as a Python dictionary
    return data

def display_students(students):
    """
    Display information about all students.
    :param students: List of student dictionaries.
    """
    print("\nAll Students:")
    for student in students:
        print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")

def filter_students_by_gpa(students, min_gpa):
    """
    Filter and display students with a GPA above the specified minimum.
    :param students: List of student dictionaries.
    :param min_gpa: Minimum GPA for filtering.
    """
    filtered_students = [s for s in students if s['gpa'] >= min_gpa]
    print(f"\nStudents with GPA >= {min_gpa}:")
    if filtered_students:
        for student in filtered_students:
            print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")
    else:
        print("No students found.")

def main():
    # Load the data from the YAML file
    data = load_data('students.yaml')
    students = data['students']
    
    # Display all students
    display_students(students)
    
    # Filter students by GPA
    min_gpa = float(input("\nEnter minimum GPA to filter students: "))
    filter_students_by_gpa(students, min_gpa)

if __name__ == "__main__":
    main()
```

### Step 4: Run the Application
1. Make sure both `app.py` and `students.yaml` are in the same directory.
2. Open your terminal, navigate to the directory, and run:

- python app.py

### Expected Output
When you run the application, you should see output similar to this:

![img](https://github.com/Panchikagupta05/Yml-file-Usecase/blob/91c8303d9f98d105dd0e65fb6d9f045ae39eec6c/Output.png)

