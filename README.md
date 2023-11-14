## Introductory Exercises
Thank you for taking our course. Completing the following tasks will prepare you for the exercise sessions in the coming weeks. Machine learning on larger scales often requires using central compute clusters, which run on Linux. Consequently, we will use workstations running Ubuntu Linux. We highly recommend to use Linux systems instead of Windows.


### Task 1: Setting up your repository.
- Configure GitHub for ssh access. You need to generate a key pair and add the public key to your GitHub account.
  - To generate your key follow the steps in: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
  - How to add a key is described here: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
- Hit the green `Code`-button in the upper right corner of this repository. Select the `SSH` tab and copy the link leading to your repository. This is necessary to clone your github repository onto your local machine.
- Open a terminal by pressing `Ctrl+Alt+T`.
- Clone this repository by running 
  ```bash
  git clone <ssh-link>
  ```
  in the terminal and substitute the `<ssh-link>` with the link you just copied. After pressing `Enter` your repository will be downloaded into your current working directory.
- Navigate into the downloaded directory by typing `cd day_01_exercise_intro-yourname`. Use `ls` to list the contents of the folder you are currently working in. If Visual Studio Code is installed correctly you can open it from the terminal by typing `code .`.

In Vscode, you can now open a rendered version of this readme. Right-click the file and select `Open Preview`.

### Task 2: Downloading and installing Miniconda.
To develop and execute our python code, we use a python container software called miniconda. Using miniconda you can create an `environment` which holds python and all the required software to run the given scripts.
- Navigate to https://docs.conda.io/en/latest/miniconda.html in your favorite browser.
The HRZ-Pool computers run Ubuntu Linux. Download the `Miniconda3 Linux 64-bit` file.

- Open the terminal on your machine by pressing `Ctrl+Alt+T`. Navigate into the Downloads folder by typing `cd Downloads`. Before running the installer, set the executable bit by typing `chmod +x Miniconda3-latest-Linux-x86_64.sh`. Install Miniconda via `./Miniconda3-latest-Linux-x86_64.sh`.
- Close your terminal and open it again. Check if you can see the `(base)` environment name on the left hand side of your command line. This means that (mini)conda is installed correctly


### Task 3: Setting up Vscode for python development
- Open Visual Studio Code.
- Click on the extensions tab in vscode (on the left hand side) or press `Ctrl+Shift+X`. Install the `Python` and `Remote-SSH` extensions. Choose the versions provided by Microsoft.
- Make the Miniconda interpreter your default in Vscode by pressing `Ctrl+Shift+P`. Type `select interpreter` and press enter. In the following dialogue, choose the `base` environment. 

### Task 4: Installing dependencies
- Open a terminal by pressing `Ctrl+Alt+T`. Navigate into this directory by typing `cd day_01_exercise_intro-yourname`. Type

  ```bash
  pip install -r requirements.txt
  ```
  to install the python packages required for this exercise.

### Task 5: Run an automatic test.
Scientific software must provide reproducible results. Automatic testing ensures our software runs reliably. We recommend Nox for test automation https://nox.thea.codes/en/stable/. 
- To run some of the tests we prepared for you type,
    ```bash
    nox -s test
    ```
  The python extension provides test integration into Vscode. To use it, click on the lab-flask icon on the left sidebar. When opening it for the first time, it asks you for a configuration.
  Click the `Configure Python Tests` button and select `pytest` in the ensuing prompt. In the next step, Vscode wants to know the location of the test folder. Choose `tests`. 
  Vscode will now display your tests on the sidebar on the left. Click the play symbol next to the tests folder to run all tests.

### Task 6: Implement and test a python class.
- Open `src/my_code.py` and finish the `__init__` function of the `Complex` class. The idea here is to implement support for complex numbers (see: https://en.wikipedia.org/wiki/Complex_number for more information about complex numbers). Double-check your code by running `nox -s test`. 

### Task 7: Breakpoints
- Click on a line number in `my_code.py`. A red dot appears. Press the `debug_test` button in the `Testing` tab, Python will pause, and you can use the build-in `Debug console` to explore the data at this point.

### Task 8: Implement the remaining functions in my_code.py
- Implement and test the `add`, `radius`, `angle`, and `multiply` functions.

### Task 9: Plotting
- Run `python ./src/julia.py` to compute a plot of the Julia set with your `Complex` class (see: https://en.wikipedia.org/wiki/Julia_set for more information).
- In `src/julia.py` use `plt.plot` and `plt.imshow` to visualize the julia-set. Feel free to play with `c` to create different sets.


### Task 10: Getting nox to help you format your code.
- Professionally written python code respects coding conventions. Type `nox -s format` to have `nox` format your code for you.

### Optional Task 11: Linting
- `nox` can do even more for you! A basic syntax error at the wrong place can cost days of computation time. Type
  ```bash
  nox -s lint
  ```
  to check your code for formatting issues and syntax errors.

### Optional Task 12: Typing
- Take a look at https://docs.python.org/3/library/typing.html . `nox` can help you by checking your code for type problems and incorrect function signatures.
  ```bash
  nox -s typing
  ```

### Final Task 13: Finishing up the task
At the end of the day after you finished all your tasks we want to save the results and upload them to your online github repository. Ideally, all the tests were successful. Follow these steps:
- Open a terminal by pressing `Ctrl+Alt+T`. Navigate into this directory using the `cd` command.
- Use
  ```bash
  git status
  ```
  to check if there are any files to commit. These are marked red.
- Add all the red files by using
  ```bash
  git add -A
  ```
- These files are now staged and can be commited. If you are commiting for the first time you will have to specify your github email address and username by typing
  ```bash
  git config --global user.email "put_your_email@here.com"
  git config --global user.name "put_your_username_here"
  ```
- Now commit the staged files with
  ```bash
  git commit -m "Final commit"
  ```
  and use your own commit message to describe the commit.
- Finally, push everything to github with
  ```bash
  git push
  ```

Alternatively, you can use Vscode to commit and push your results. 
- For that, go to your code in Vscode and open the source control tab on the left hand side or press `Ctrl+Shift+G`. 
- In the window that opens up enter your individual commit message and press `Ctrl+Enter` to commit to the main branch.
- Vscode might ask if you want to stage files that haven't been staged yet. Continue with `yes`. You can also stage files by using the plus sign next to the file.
- Finally, push everything by hitting the `Sync Changes` button.
