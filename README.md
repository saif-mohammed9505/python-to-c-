# Python to C++ Code Converter

An AI-powered Python to C++ code conversion tool that uses Large Language Models (LLMs) to generate high-performance C++ code from Python code.

The project also allows the generated C++ code to be compiled and executed locally using a C++ compiler, with an interactive Gradio interface.

## Features

- Convert Python code into C++ code using AI
- Support for multiple LLM options:
  - DeepSeek
  - Llama 3.2
- Uses system information to help generate C++ code optimized for the local machine
- Automatically generates a `main.cpp` file
- Compile generated C++ code using `g++`
- Execute the compiled C++ program
- Run Python code and view its output
- Compare Python and C++ execution results
- Interactive Gradio user interface
- Uses optimization flags for faster C++ execution

## Project Workflow

```text
Python Code
     │
     ▼
Select AI Model
     │
     ├── DeepSeek
     │
     └── Llama 3.2
     │
     ▼
AI converts Python → C++
     │
     ▼
Generated C++ Code
     │
     ▼
main.cpp
     │
     ▼
g++ Compiler
     │
     ▼
main.exe
     │
     ▼
C++ Output
```

# Python to C++ Code Converter

An AI-powered tool that converts Python code into C++ code using Large Language Models (LLMs). The project also allows the generated C++ code to be compiled and executed locally.

## Technologies Used

- Python
- C++
- OpenAI Python SDK
- OpenRouter
- Hugging Face
- Ollama
- DeepSeek
- Llama 3.2
- Gradio
- Jupyter Notebook
- MSYS2 / UCRT64
- g++

## Features

- Convert Python code into C++ using AI
- Support for DeepSeek and Llama 3.2
- Retrieve local system information
- Generate C++ code automatically
- Save generated code as `main.cpp`
- Compile generated C++ code using `g++`
- Execute generated C++ programs
- Run Python code and display its output
- Display C++ execution output
- Interactive Gradio interface
- Compare Python and C++ execution performance
- Use C++ compiler optimization flags

## How It Works

Python Code → AI Model → Generated C++ → `main.cpp` → g++ → `main.exe` → Output

The project retrieves information about the local system and provides it to the AI model. The selected model then converts the Python code into C++. The generated C++ code can be compiled and executed locally.

## Requirements

Install the required Python packages:

    pip install -r requirements.txt

### requirements.txt

    openai
    python-dotenv
    huggingface-hub
    ipython
    gradio

A C++ compiler is also required.

This project uses:

- MSYS2
- UCRT64
- g++

The compiler path used in the notebook is:

    C:\msys64\ucrt64\bin\g++.exe

## AI Models

### DeepSeek

    deepseek-ai/DeepSeek-V3-0324

### Llama 3.2

    llama3.2

Llama 3.2 can be run locally using Ollama.

Install the model using:

    ollama pull llama3.2

## Environment Variables

Create a `.env` file in the project directory:

    OPENROUTER_API_KEY=your_openrouter_api_key
    HF_TOKEN=your_huggingface_token

Do not upload `.env` or API keys to GitHub.

## Project Structure

    python-to-cpp/
    │
    ├── python_to_c++.ipynb
    ├── system_info.py
    ├── requirements.txt
    ├── .gitignore
    ├── README.md
    │
    └── Generated Files
        ├── main.cpp
        └── main.exe

`main.cpp` and `main.exe` are generated during execution and should not be committed to GitHub.

## Gradio Interface

The project provides an interactive Gradio interface with:

- Python code input
- C++ code output
- AI model selection
- Run Python button
- Convert button
- Run C++ button
- Python output
- C++ output

The workflow is:

    Python Code
         │
         ├── Run Python ──→ Python Output
         │
         └── Select Model
                  │
                  ▼
               Convert
                  │
                  ▼
            Generated C++
                  │
                  ▼
               Run C++
                  │
                  ▼
              C++ Output

## C++ Compilation

The generated C++ code is compiled using `g++`.

Example:

    g++ -std=c++17 -Ofast main.cpp -o main.exe

The project can also use additional optimization flags:

    -Ofast
    -march=native
    -flto
    -fvisibility=hidden
    -DNDEBUG

## Example

### Python

    import time

    def calculate(iterations, param1, param2):
        result = 1.0

        for i in range(1, iterations + 1):
            j = i * param1 - param2
            result -= (1 / j)

            j = i * param1 + param2
            result += (1 / j)

        return result

    start_time = time.time()

    result = calculate(200_000_000, 4, 1) * 4

    end_time = time.time()

    print(f"Result: {result:.12f}")
    print(f"Execution Time: {(end_time - start_time):.6f} seconds")

### Generated C++

    #include <iostream>
    #include <chrono>

    double calculate(int iterations, double param1, double param2) {
        double result = 1.0;

        for (int i = 1; i <= iterations; ++i) {
            double j = i * param1 - param2;
            result -= (1.0 / j);

            j = i * param1 + param2;
            result += (1.0 / j);
        }

        return result;
    }

    int main() {
        auto start_time = std::chrono::high_resolution_clock::now();

        double result = calculate(200000000, 4.0, 1.0) * 4.0;

        auto end_time = std::chrono::high_resolution_clock::now();

        std::chrono::duration<double> duration = end_time - start_time;

        std::cout.precision(12);
        std::cout << "Result: " << result << std::endl;

        std::cout.precision(6);
        std::cout << "Execution Time: "
                  << duration.count()
                  << " seconds" << std::endl;

        return 0;
    }

## Performance Example

In the notebook, the Python implementation produced approximately:

    Result: 3.141592656089
    Execution Time: 39.486653 seconds

The generated C++ implementation produced approximately:

    Result: 3.14159265654
    Execution Time: 0.289723 seconds

Actual execution time may vary depending on the computer, compiler, optimization settings, and generated code.

## Installation

### 1. Clone the Repository

    git clone https://github.com/YOUR_USERNAME/python-to-cpp.git
    cd python-to-cpp

### 2. Create a Virtual Environment

    python -m venv .venv

Activate it on Windows:

    .venv\Scripts\activate

### 3. Install Dependencies

    pip install -r requirements.txt

### 4. Configure API Keys

Create a `.env` file:

    OPENROUTER_API_KEY=your_openrouter_api_key
    HF_TOKEN=your_huggingface_token

### 5. Start Jupyter Notebook

    jupyter notebook

Open:

    python_to_c++.ipynb

Run the notebook cells in order.

### 6. Launch the Gradio Interface

The notebook starts a local Gradio application.

It will provide a local URL similar to:

    http://127.0.0.1:xxxx

Open the URL in your browser.

## Important Notes

- AI-generated C++ code should be tested before use.
- Generated code may not always be correct for every Python program.
- Python and C++ have different language features and runtime behavior.
- A C++ compiler is required to compile and execute the generated code.
- Execution time depends on the local machine and generated implementation.
- The project is intended for educational and experimental purposes.
- Generated executable files should not be uploaded to GitHub.

## Security

Never commit API keys or secrets to GitHub.

The following files should remain local:

    .env
    .venv/
    main.exe

These files should be excluded using `.gitignore`.

## Future Improvements

- Improve Python-to-C++ conversion accuracy
- Add support for more AI models
- Support more Python libraries
- Add automatic correctness testing
- Add automatic performance benchmarking
- Improve compiler detection
- Add cross-platform compiler support
- Add downloadable C++ files
- Improve compilation error handling
- Add more optimization strategies

## 📌 Repository

GitHub Repository:

https://github.com/saif-mohammed9505/python-to-c-

---

## 👨‍💻 Author

**Saif Mohammed**

GitHub:

https://github.com/saif-mohammed9505

---

## License

This project is intended for educational and experimental purposes.
