## Setting Up Git and Cloning a Repository

### Introduction

It is important to know how to clone a git repository from GitHub. There are several ways to do this, but in a professional setting this is often done securely via Secure Shell (SSH). This requires some setup which we will complete here and then move on to clone the course syllabus as a first task.

### How To Set Up Git

Providing your email helps Git track who changed what file. Git will eventually ask you for this information, but you can use the following commands to set it up ahead of time.

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

### Optional: How to Set Up SSH Keys

Git provides multiple options for cloning repositories. In this class we will use HTTPS. If you wish to use SSH instead, you may optionally do the following steps.

To set up your SSH keys, first open Git Bash or the shell you are using for this class and then run the following command to generate a key.

```bash
ssh-keygen -t ed25519 -C ""
```

You can leave all fields blank, even the password, for this exercise. This will generate a public and a private key. You want to print (cat) the public key to your screen. In Git Bash or your preferred shell, do the following.

```bash
cat $HOME/.ssh/id_ed25519.pub
```

This will print the public key to your screen. Copy that key text.

Go to [https://github.com/settings/ssh/new](https://github.com/settings/ssh/new) and paste the public key. Give it a descriptive name.

### Clone the Syllabus

You are now ready to clone the course syllabus!

Go to a web browser and navigate to the syllabus page: [https://github.com/ruc-practical-ai-fall-2025/syllabus](https://github.com/ruc-practical-ai-fall-2025/syllabus).

Then click the green `Code` button, click HTTPS, and copy the text there. Run the following command in Git Bash or your preferred shell to clone the repository.

```bash
git clone PASTED-TEXT
```

Replace the PASTED-TEXT with the text you copied from the drop down under `Code` on GitHub. The actual command you run should look something like the following (but not exactly since the path will be different).

```bash
git clone git@github.com:ruc-practical-ai/syllabus.git
```

Be sure to do this in an area you have permissions to write, such as your home area. You can get to your home area with the following command.

```bash
cd ~
```

Finally, you can open the syllabus in VS Code by navigating to the directory using the `cd` command and then opening VS Code using `code .`. The `.` tells VS Code to open in the current directory.

```bash
cd SYLLABUS-DIRECTORY # Change to directory with this year's syllabus
code .
```

Click on the `README.md` file to open it. There is a preview button in the top right corner of VS Code's screen which should allow you to view the file the same way it is viewed on the internet.

## Optional: How to Make Your Own Repository

### Introduction

It is useful know how to make your own Git repository and host it in GitHub. While the assignments in this course will exist as Git repositories that are already made for you, you might want to work on a tool, a personal project, or other assignments as Git repositories. Professionally, you can use GitHub projects as a way to showcase your skills to prospective employers.

### Making the Repository

Navigate to your public GitHub page in your web browser by typing `https://github.com/YOUR-USERNAME`. Click on `Repositories`.

If you've never made a repository before then this page should be empty. Click the `New` button.

Give the repository a basic but descriptive name, such as "example" or "hello-world". Give it a description such as "Example repository for educational use."

Make the repository Public or Private. (You only get a set number of Private repositories when using the free version of GitHub so it is a good idea to use them sparingly.)

Add a .gitignore template. Choose the `Python` option in the dropdown. The .gitignore file tells Git which files *not* to track. It is important for professional repositories to always have an appropriate .gitignore to prevent Git from tracking unnecessary (or worse, private) files. Add a README.md file.

Leave the license set to `None` for now. Licenses are important when writing software personally or professionally but are outside the scope of this tutorial.

Click `Create repository` to create your first repository!

### Cloning the Repository

As we did above, clone the repository you just created. Do this by navigating to the repository page. For example, if you named your repository "example" you can find it at `https://github.com/YOUR-USERNAME/example`. Click the green `Code` button to grab the repository name you need to clone it. Use HTTPS unless you set up SSH.

Clone the file with the following commands.

```bash
git clone PASTED-TEXT
```

Replace the PASTED-TEXT with the text you copied from the drop down under `Code` on GitHub. The actual command you run should look something like the following.

```bash
git clone git@github.com:YOUR-USERNAME/example.git
```

### Adding Files to the Repository

Once you have cloned the repository, navigate into it with `cd`.

```bash
cd example
```

Use VS Code or the command line to create a file called `hello.py`. Populate the file with the following text.

```python
print("Hello World!")
```

Save the file. Take a moment to view the contents of the .gitignore file. Edit the README.md file if you wish.

### Pushing Back Up to GitHub

When ready, push your files back up to GitHub.

```bash
git status
git add .
git commit -m "Add hello.py"
git push
git status
```

Navigate back to your repository in your web browser to see your file there!
