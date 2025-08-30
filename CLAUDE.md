# Python Learning Resources Project

## Overview
This repository contains converted markdown versions of comprehensive Python learning guides, originally written in LaTeX. The guides are designed for beginners (minimum age 9) and cover fundamental Python topics.

## Source References

### LaTeX Source Repositories
- **Intro to Python Guide**: `/Users/hyosangahn/theCoderSchool/Intro-to-Python-Review-Guide/`
  - Contains LaTeX source files for the main Python introduction guide
  - Files include: hello_world.tex, variables.tex, if_elif_else.tex, loops.tex, collections.tex, functions.tex, miscellaneous.tex
  
- **Python OOP Guide**: `/Users/hyosangahn/theCoderSchool/Python-OOP-Turtle-Pygame/`
  - Contains LaTeX source files for the Object-Oriented Programming guide
  - Files include: classes.tex, objects.tex, oop.tex, oop_principles.tex, turtle.tex, pygame.tex

## Conversion Workflow

### From LaTeX to Markdown
1. Read LaTeX source files from the referenced repositories
2. Convert LaTeX formatting to GitHub-flavored markdown
3. Maintain consistent formatting standards:
   - Python code blocks with syntax highlighting
   - Proper heading structure
   - Clear examples and explanations
   - Navigation between chapters

### Formatting Standards
- **Bold keywords**: Vocabulary terms that should be defined
- **Emphasized text**: Important phrases for attention
- **Code blocks**: Use ```python for Python code examples
- **Headers**: Use consistent H1, H2, H3 structure
- **Links**: Internal navigation between chapters and back to table of contents
- **Comments**: Combine truncated multi-line comments from LaTeX into single line for readability

## File Structure
- `README.md` - Main landing page with navigation buttons
- `table-of-contents.md` - Interactive table of contents with chapter links
- `chapter-01.md` - Hello World (Print Statements, Comments)
- `chapter-02.md` - Variables and Data Types
- Additional chapters to be created as needed

## GitHub Pages
This repository is configured for GitHub Pages to provide web access to the learning materials alongside the PDF versions.