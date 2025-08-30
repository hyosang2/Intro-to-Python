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
  - Files include: oop.tex, classes.tex, objects.tex, oop_principles.tex, import.tex, turtle.tex, pygame.tex

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

### Intro to Python Guide (`Intro-to-Python/`)
- `table-of-contents.md` - Interactive table of contents
- `chapter-01.md` - Hello World (Print Statements, Comments)
- `chapter-02.md` - Variables and Data Types (Data types, Operators)
- `chapter-03.md` - If/Elif/Else Statements (Conditions, Logical operators)
- `chapter-04.md` - Loops (While/for loops, range(), break/continue)
- `chapter-05.md` - Collections (Strings, Lists, Tuples, Dictionaries, Sets)
- `chapter-06.md` - Functions (Function structure, Return statements)
- `chapter-07.md` - Miscellaneous Topics (Built-in functions, Libraries)

### Python OOP Guide (`Python-OOP-Turtle-Pygame/`)
- `table-of-contents.md` - Interactive table of contents
- `chapter-01.md` - OOP Introduction
- `chapter-02.md` - Classes (Class variables, __init__ method, Instance methods)
- `chapter-03.md` - Objects (Instantiation, Objects as variables)
- `chapter-04.md` - OOP Principles (Inheritance, Polymorphism, Encapsulation)
- `chapter-05.md` - Import and Modules (Placeholder)
- `chapter-06.md` - Turtle Graphics (Placeholder)
- `chapter-07.md` - Pygame Development (Placeholder)

## Updating Guides

### When LaTeX Source Files Change

#### For Existing Chapters:
1. **Identify Changed Files**: Check which `.tex` files in the source repositories have been modified
2. **Read Updated Content**: Use Read tool to examine the updated LaTeX content
3. **Convert to Markdown**: Follow the conversion standards to update the corresponding `chapter-XX.md` file
4. **Maintain Navigation**: Ensure chapter navigation links remain intact
5. **Preserve Jekyll Front Matter**: Keep the YAML front matter at the top of each file

#### For New Chapters:
1. **Create New Chapter File**: Create `chapter-XX.md` in the appropriate guide folder
2. **Add Jekyll Front Matter**:
   ```yaml
   ---
   layout: default
   title: Chapter X - Title
   ---
   ```
3. **Convert LaTeX Content**: Follow formatting standards from existing chapters
4. **Update Table of Contents**: Add new chapter link to `table-of-contents.md`
5. **Update Navigation**: Add previous/next links in adjacent chapters
6. **Update README.md**: If it's a completely new guide, add section to main README

#### For New Guides:
1. **Create New Folder**: Create `New-Guide-Name/` folder in repository root
2. **Create Table of Contents**: Create `table-of-contents.md` with Jekyll front matter and navigation
3. **Convert All Chapters**: Create individual chapter files following existing patterns
4. **Update Main README.md**: Add new guide section with simple text links format:
   ```markdown
   ### 📚 New Guide Name
   Description of the new guide.
   
   [📖 Table of Contents](New-Guide-Name/table-of-contents.md)
   
   [📄 Download PDF](link-to-pdf)
   ```
5. **Update _config.yml**: Ensure new folders are included in Jekyll processing

### Important Notes:
- **Always use .md extensions** in internal links for GitHub Pages compatibility
- **Maintain Jekyll front matter** in all chapter files
- **Use simple text links** rather than button badges for better GitHub Pages reliability
- **Test navigation** after updates to ensure all links work correctly
- **Keep formatting consistent** with existing chapters

## GitHub Pages
This repository is configured for GitHub Pages using the Cayman theme with jekyll-relative-links plugin for proper markdown link processing.