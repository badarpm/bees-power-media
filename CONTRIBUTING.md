# Contributing to Bee's Power Media 🐝

First off, thank you for considering contributing! Every contribution helps make this tool better for everyone.

## 🤔 How Can I Contribute?

### Reporting Bugs 🐛
Found a bug? Help us squash it!

1. **Check existing issues** - Someone might have already reported it
2. **Create a new issue** using the "Bug Report" template
3. **Include:**
   - Clear, descriptive title
   - Steps to reproduce
   - Expected vs actual behavior
   - Screenshots if applicable
   - Your environment (Windows version, Python version)

### Suggesting Features 💡
Have an idea? We'd love to hear it!

1. **Check existing issues** - It might already be planned
2. **Create a new issue** using the "Feature Request" template
3. **Describe:**
   - The problem you're trying to solve
   - Your proposed solution
   - Why this would be useful to others

### Submitting Code 🔧

#### First-Time Contributors
1. **Fork** the repository
2. **Clone** your fork:
```bash
   git clone - Contact the maintainer: badarpm (badarjamal@hotmail.com).git
```
3. **Create a branch** for your feature:
```bash
   git checkout -b feature/amazing-new-feature
```
4. **Make your changes**
5. **Test thoroughly**
6. **Commit** with clear message:
```bash
   git commit -m "Add amazing new feature"
```
7. **Push** to your fork:
```bash
   git push origin feature/amazing-new-feature
```
8. **Open a Pull Request** on the main repository

#### Pull Request Guidelines
✅ **DO:**
- Write clear, descriptive commit messages
- Add tests for new features
- Update documentation if needed
- Follow existing code style
- Keep PRs focused (one feature/fix per PR)

❌ **DON'T:**
- Submit large PRs without discussion first
- Break existing functionality
- Ignore code review feedback
- Include unrelated changes

## 📝 Code Style

### Python Style Guide
- Follow **PEP 8** guidelines
- Use **type hints** where appropriate
- Write **docstrings** for all public functions
- Keep functions **under 50 lines** when possible
- Use **meaningful variable names** (no single letters except in loops)

### Example:
```python
def convert_media_file(
    input_path: str,
    output_format: str,
    start_time: str = "00:00:00"
) -> bool:
    """
    Convert media file to specified format.
    
    Args:
        input_path: Path to source media file
        output_format: Desired output format (e.g., "MP4", "MKV")
        start_time: Trim start time in HH:MM:SS format
    
    Returns:
        True if conversion successful, False otherwise
    """
    # Implementation here
    pass
```

## 🧪 Testing

Before submitting:
```bash
# Run all tests
pytest

# Check code style
flake8 src/

# Format code
black src/
```

## 📚 Documentation

- Update `README.md` if adding new features
- Add docstrings to new functions/classes
- Update user guide if changing UI/UX
- Comment complex logic

## 🏷️ Commit Message Format
```
type(scope): brief description

Detailed explanation if needed

Fixes #123
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation only
- `style`: Formatting, missing semicolons, etc.
- `refactor`: Code restructuring
- `test`: Adding tests
- `chore`: Maintenance tasks

**Example:**
```
feat(converter): add WebM format support

Implemented WebM container format conversion using FFmpeg.
Includes unit tests and updated format dropdown.

Fixes #42
```

## ❓ Questions?

- Open a [GitHub Discussion](https://github.com/badarpm/bees-power-media/discussions)
- Check existing [Issues](https://github.com/badarpm/bees-power-media/issues)
- Contact maintainers -badarpm (badarjamal@hotmail.com)

---

**Thank you for contributing to Bee's Power Media! 🐝🍯**
