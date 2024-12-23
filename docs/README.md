# genfunc

[![PyPI version](https://badge.fury.io/py/genfunc.svg)](https://badge.fury.io/py/genfunc)
[![Python Support](https://img.shields.io/pypi/pyversions/genfunc.svg)](https://pypi.org/project/genfunc/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

genfunc is a powerful Python package that leverages Large Language Models (LLMs) to automatically generate, manage, and execute Python functions. Simply describe what you want your function to do, and genfunc will create it for you.

### Ideal Usecase 

The ideal use case for the this package is to leverage LLMs to automatically generate, manage, and execute Python functions based on user-provided descriptions. This can be particularly useful for:

- Rapid prototyping and development
- Automating repetitive coding tasks
- Generating boilerplate code
- Creating utility functions on-the-fly
- Enhancing productivity by reducing manual coding effort

## 🚀 Features

- 🤖 Automatic function generation using state-of-the-art LLMs
- 🔄 Support for multiple LLM providers (OpenAI, Anthropic)
- 🔒 Secure API key handling
- 📁 Automatic function storage and management
- ⚡ Immediate function execution capability
- 🛡️ Comprehensive error handling and logging
- 🧪 Extensive test coverage

## 📋 Requirements

- Python 3.8 or higher
- Valid API key for at least one supported LLM provider (OpenAI or Anthropic)

## 💻 Installation

```bash
pip install genfunc
```

### Additional Dependencies (of your choice, atleast one) -

```bash
pip install openai
```
or
```bash
pip install anthropic
```

## 🔧 Configuration

Before using func, you need to configure your LLM provider API keys. You have two options:

### Option 1: Environment Variables

```bash
export OPENAI_API_KEY=your_openai_api_key
export ANTHROPIC_API_KEY=your_anthropic_api_key
```

### Option 2: .env File

Create a `.env` file in your project root:

```env
OPENAI_API_KEY=your_openai_api_key
ANTHROPIC_API_KEY=your_anthropic_api_key
```

## 🎯 Quick Start

Here's a simple example to get you started:

```python
from genfunc import func

# Initialize with OpenAI
func.initialize(provider="openai")

# Generate a function without calling it
func.generate("Create a function that calculates the factorial of a number")

# import the function 
from helpers.file_name import function_name
```

Alternatively,

```python
# Generate and immediately call a function
result = func.generate(
    "Create a function that adds two numbers", 
    call=True, # calls the function
    a=5, # arg1
    b=3  # arg2
)

print(result)  # Output: 8
```

## 📖 Detailed Usage

### Initialization

You can initialize func with different providers:

```python
# Initialize with OpenAI
func.initialize(provider="openai", api_key="your_api_key")

# Initialize with Anthropic
func.initialize(provider="anthropic", api_key="your_api_key")
```

### Function Generation

func offers two modes of function generation:

1. Generate Only:
```python
# This will create the function and save it to ./helpers/
func.generate("Create a function that converts temperature from Celsius to Fahrenheit")
```

2. Generate and Execute:
```python
# This will create the function, save it, and immediately execute it
result = func.generate(
    "Create a function that calculates the area of a circle",
    call=True,
    radius=5
)
print(result)  # Output: 78.53981633974483
```

### Function Storage

Generated functions are automatically stored in the `./helpers/` directory. Each function is saved in its own Python file, making it easy to:
- Review generated code
- Modify functions if needed
- Import functions into other projects
- Version control your generated functions

### Advanced Usage

#### Custom Provider Configuration

```python
func.initialize(
    provider="openai",
    api_key="your_api_key",
    model="gpt-4o"  # Specify model version
)
```

## 🔍 Examples

### Data Processing Function

```python
# Generate a data processing function
func.generate("""
Create a function that takes a pandas DataFrame with columns 'date' and 'value',
and returns the moving average with a window of 7 days
""")
```

### Algorithm Implementation

```python
# Generate a sorting algorithm
result = func.generate(
    "Create a function that implements the quicksort algorithm",
    call=True,
    arr=[3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
)
print(result)  # Output: [1, 1, 2, 3, 3, 4, 5, 5, 5, 6, 9]
```

### API Integration

```python
# Generate an API wrapper function
func.generate("""
Create a function that takes a city name and returns the current weather
using the OpenWeatherMap API
""")
```

*View more examples [here](examples.md)*

## 🧪 Testing

Run the test suite:

```bash
# Install dev dependencies
pip install -e ".[dev]"

# Run tests
pytest

# Run tests with coverage
pytest --cov=func tests/
```

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

Please make sure to update tests as appropriate and adhere to the existing coding style.

*View more details [here](contributing.md)*

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- OpenAI for their GPT models
- Anthropic for Claude
- All contributors who have helped shape this project

## 📚 Documentation

For more detailed documentation, visit our [documentation site](https://func.readthedocs.io/).

## 🔗 Links

- [PyPI Package](https://pypi.org/project/func/)
- [GitHub Repository](https://github.com/argishh/func)
- [Issue Tracker](https://github.com/argishh/func/issues)
- [Change Log](CHANGELOG.md)

## 🤔 FAQ

**Q: Is there a limit to how complex the generated functions can be?** \
A: The complexity limit depends on the LLM provider's token limits and capabilities. Generally, func works best with focused, single-purpose functions.

**Q: Can I modify the generated functions?** \
A: Yes! Generated functions are stored as regular Python files in the `./helpers/` directory and can be modified like any other Python code.

**Q: How secure is my API key?** \
A: API keys are handled securely through environment variables or `.env` files. They are never stored in the generated code or exposed in any way.

## ⚠️ Known Issues

- Very long function descriptions might be truncated by LLM token limits
- Some complex mathematical operations might require manual verification
- Generated functions might need optimization for production use

## 🗺️ Roadmap (to-do)

- [ ] Add support for more LLM providers
- [ ] Implement function optimization suggestions
- [ ] Add type hint generation
- [ ] Create a web interface for function generation
- [ ] Add support for async functions
- [ ] Implement function chaining

## 📊 Stats

- Release Date: 04-12-2024
- Latest Version: 0.1.0
- Python Versions: 3.8+

---

Made with ❤️ by Argish