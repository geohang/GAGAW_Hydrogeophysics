# Contributing to GAGAW_Hydrogeophysics

Thank you for your interest in contributing to GAGAW_Hydrogeophysics! This project demonstrates practical applications of PyHydroGeophysX for field hydrogeophysical data analysis.

## 🤝 How to Contribute

### Reporting Issues

If you find a bug or have a suggestion:

1. Check if the issue already exists in [Issues](https://github.com/yourusername/GAGAW_Hydrogeophysics/issues)
2. If not, create a new issue with:
   - Clear title and description
   - Steps to reproduce (for bugs)
   - Expected vs actual behavior
   - System information (OS, Python version, PyHydroGeophysX version)
   - Relevant code snippets or error messages

### Suggesting Enhancements

We welcome ideas for:
- New workflow examples
- Additional field datasets
- Improved documentation
- Better visualizations
- Performance optimizations

Please open an issue with the "enhancement" label and describe:
- The motivation for the enhancement
- How it would benefit users
- Potential implementation approach

### Contributing Code

#### Getting Started

1. **Fork the repository** on GitHub

2. **Clone your fork**:
   ```bash
   git clone https://github.com/yourusername/GAGAW_Hydrogeophysics.git
   cd GAGAW_Hydrogeophysics
   ```

3. **Create a new branch**:
   ```bash
   git checkout -b feature/your-feature-name
   ```

4. **Set up development environment**:
   ```bash
   pip install -r requirements.txt
   ```

#### Making Changes

1. **Write clear, documented code**:
   - Follow existing code style
   - Add comments for complex logic
   - Include docstrings for functions

2. **Test your changes**:
   - Run existing notebooks to ensure no regressions
   - Test with different data configurations
   - Verify outputs in the results/ directory

3. **Update documentation**:
   - Update README.md if adding new workflows
   - Add comments to notebooks explaining new features
   - Update requirements.txt if adding dependencies

4. **Commit your changes**:
   ```bash
   git add .
   git commit -m "Add feature: brief description"
   ```
   
   Commit message guidelines:
   - Use present tense ("Add feature" not "Added feature")
   - Start with capital letter
   - Be specific but concise

5. **Push to your fork**:
   ```bash
   git push origin feature/your-feature-name
   ```

6. **Create a Pull Request**:
   - Go to the original repository on GitHub
   - Click "New Pull Request"
   - Select your fork and branch
   - Fill in the PR template with:
     - Description of changes
     - Related issue numbers
     - Testing performed
     - Screenshots (if applicable)

#### Code Review Process

- Maintainers will review your PR
- Address any feedback or requested changes
- Once approved, your PR will be merged

### Contributing Data

If you have field data to share:

1. **Ensure you have permission** to share the data
2. **Document the data** including:
   - Site location and description
   - Acquisition parameters
   - Data format and units
   - Any preprocessing applied
3. **Open an issue** describing the dataset
4. Discuss with maintainers about data hosting and integration

### Contributing Documentation

Documentation improvements are always welcome:

- Fix typos or unclear explanations
- Add more detailed examples
- Improve workflow descriptions
- Translate documentation (if applicable)

## 📝 Style Guidelines

### Python Code

- Follow [PEP 8](https://pep8.org/) style guide
- Maximum line length: 88 characters (Black formatter standard)
- Use meaningful variable names
- Add type hints where helpful

### Jupyter Notebooks

- Include markdown cells explaining each step
- Keep code cells focused (one task per cell)
- Clear all outputs before committing (use "Restart & Clear Output")
- Add visualizations with appropriate labels and titles

### Documentation

- Use Markdown for documentation files
- Keep lines to ~80 characters for readability
- Use clear section headers with appropriate levels
- Include code examples in triple backticks with language tags

## 🔍 Testing

Before submitting a PR:

1. **Run notebooks end-to-end**:
   ```bash
   jupyter nbconvert --to notebook --execute your_notebook.ipynb
   ```

2. **Check for errors** in outputs and results

3. **Verify file paths** work on different systems

4. **Test with different LLM providers** (if applicable)

## 📋 Pull Request Checklist

- [ ] Code follows style guidelines
- [ ] Comments added for complex sections
- [ ] Documentation updated (README, docstrings, etc.)
- [ ] Notebooks run without errors
- [ ] No unnecessary files committed (check .gitignore)
- [ ] Commit messages are clear and descriptive
- [ ] PR description explains what and why

## 🐛 Reporting Security Issues

If you discover a security vulnerability:

1. **Do NOT** open a public issue
2. Email the maintainers directly
3. Include detailed steps to reproduce
4. Allow time for a fix before public disclosure

## 💬 Questions?

- Open a [Discussion](https://github.com/yourusername/GAGAW_Hydrogeophysics/discussions) for general questions
- Check existing [Issues](https://github.com/yourusername/GAGAW_Hydrogeophysics/issues) and [Discussions](https://github.com/yourusername/GAGAW_Hydrogeophysics/discussions)
- Refer to [PyHydroGeophysX documentation](https://github.com/geohang/PyHydroGeophysX) for package-specific questions

## 📜 License

By contributing, you agree that your contributions will be licensed under the Apache License 2.0.

## 🙏 Recognition

Contributors will be acknowledged in the README.md file. Significant contributions may be mentioned in publications using this code.

Thank you for contributing to GAGAW_Hydrogeophysics!
