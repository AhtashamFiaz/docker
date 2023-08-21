**Workflow: Cloning, Making Changes, Merging, and Pre-Commit and post-commit Hook Setup**
Clone the Repository
git clone 
Create and Modify a Text File
nano text.txt
Make your desired changes within the `text.txt` file using the `nano` text editor.
Stage and Commit the Changes:
git add text.txt
git commit -m "ahtasham, welcome
Merge Branch to Main:
git checkout main
git pull origin main
git merge new
git push origin main
**Set Up Pre-Commit Hook:**
Inside the repository, navigate to the `.git/hooks` directory and create a file named `pre-commit`:

6. **Add Pre-Commit Bash Script:**
Open the newly created `pre-commit` file and insert the following script:
```bash
#!/bin/bash

# Prevent trailing whitespace
if git diff --check --cached | grep -q "^\+.*[[:blank:]]$"; then
    echo "Error: Trailing whitespace detected. Please remove before committing."
    exit 1
fi

# Prevent console.log statements
if git diff --cached | grep -q "^\+.*console\.log"; then
    echo "Error: console.log statements detected. Please remove before committing."
    exit 1
fi

exit 0
Make the Pre-Commit Script Executable:
chmod +x .git/hooks/pre-commit
Test the Pre-Commit Script:
Create a test file, e.g., readme.md, within the repository. Add trailing whitespace or a console.log statement to the file, then attempt to commit the changes. The script should prevent the commit if the conditions are not met.

Post-Commit Script (Optional):
To set up a post-commit script, follow a similar process as the pre-commit script. Create a file named post-commit in the .git/hooks directory, add your desired script content, and make it executable.
