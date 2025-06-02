import subprocess
import os
import re
from openai import OpenAI

# Step 1: Parse User Prompt
def parse_user_prompt(prompt):
    # Validate and sanitize the user prompt
    if not isinstance(prompt, str) or len(prompt.strip()) == 0:
        raise ValueError("Invalid prompt: Prompt must be a non-empty string.")
    
    print(f"Parsing user prompt: {prompt}")
    # For simplicity, return mock requirements
    return {"language": "Python", "features": ["basic calculator"]}

# Step 2: Generate Code
def generate_code(requirements):
    print(f"Generating code for: {requirements}")
    # Mock code generation (replace with OpenAI Codex or GPT-4 API calls)
    code = """
def calculator():
    while True:
        operation = input("Enter operation (+, -, *, /) or 'exit': ").strip()
        if operation == 'exit':
            print("Exiting calculator.")
            break
        if operation not in ('+', '-', '*', '/'):
            print("Invalid operation. Please use one of (+, -, *, /) or 'exit'.")
            continue
        try:
            x = float(input("Enter first number: ").strip())
            y = float(input("Enter second number: ").strip())
            if operation == '+':
                print(f"Result: {x + y}")
            elif operation == '-':
                print(f"Result: {x - y}")
            elif operation == '*':
                print(f"Result: {x * y}")
            elif operation == '/':
                if y == 0:
                    print("Error: Division by zero is not allowed.")
                else:
                    print(f"Result: {x / y}")
        except ValueError:
            print("Invalid input. Please enter numeric values.")
calculator()
"""
    return code

# Step 3: Save Code to File
def save_code(code, filename="generated_app.py"):
    # Validate filename to prevent directory traversal attacks
    if not re.match(r'^[\w\-\.]+$', filename):
        raise ValueError("Invalid filename: Filename must consist of alphanumeric characters, dashes, underscores, or dots.")
    
    with open(filename, "w") as file:
        file.write(code)
    print(f"Code saved to {filename}")

# Step 4: Test Run the Code
def test_run_code(filename="generated_app.py"):
    # Validate filename before running it as a subprocess
    if not os.path.exists(filename):
        raise FileNotFoundError(f"File not found: {filename}")
    if not filename.endswith(".py"):
        raise ValueError("Invalid file type: Only Python files are allowed for execution.")

    try:
        print(f"Running {filename}...")
        result = subprocess.run(["python3", filename], capture_output=True, text=True, check=True)
        print("Output:\n", result.stdout)
        print("Errors:\n", result.stderr if result.stderr else "No errors")
    except subprocess.CalledProcessError as e:
        print(f"Subprocess error: {e}")
    except Exception as e:
        print(f"Error during test run: {e}")

# Main Workflow
def main(prompt):
    try:
        requirements = parse_user_prompt(prompt)
        code = generate_code(requirements)
        save_code(code)
        test_run_code()
    except Exception as e:
        print(f"An error occurred: {e}")

# Example Usage
user_prompt = "Create a basic calculator app in Python"
main(user_prompt)