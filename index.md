# Bryce Whitney Introduction Page

## Introduction

My name is Bryce Whitney and I am a senior at William & Mary. I am a Computer Science and Data Science double major, and outside the classroom I am the president of the Men's Club Ultimate team and spend a lot of time playing with them. Below is a nice selfie I took a while back:

<p align="center">
    <img src="selfie.jpg" width="200"/>
</p>

## Sample Script

Below is a sample script I created called `randomPassword.py`. It uses a combination of letters (both uppercase and lowercase) and numbers to create a random password which has a length determined by the user (Default is 10 characters). This is designed to be used in terminal where a user can determine the length of a password and set a random seed if they would like using the command 'python randomPassword.py -l [length] -r [random seed]' and replacing 'length' and 'random seed' with their desired quantities. This allows users to generate a password for websites and all they need to store is the random seed so they can regenerate the password if they forget it. 

```python
#############################################################################################
# File Name: randomPassword.py                                                              #
# Python Version: 3.8.10                                                                    #
#                                                                                           #
# Author: Bryce Whitney                                                                     #
# Last Edit: September 15, 2021                                                             #
#                                                                                           #
# Generates a random password using letters (uppercase and lowercase), numbers, and symbols #
#############################################################################################


# Required Imports
import string
import random
import argparse


def generatePassword(passwordLength=10, randomSeed=None):
    """
    Generates a random password of the length provided in the command line. If no length is given, the default is 8 characters. 
    The user can also pass a random seed argument so they can reproduce their results. This way they can track the seeds they used
    in a seperate file and regenerate their password when they forget it. 

    Arguments:
        passwordLength [int] -- Length of the desired password. 10 characters by deafult. 
        randomSeed     [int] -- The random seed to be used. None by deafult.
    """
    # Create sets of characters
    LETTERS = string.ascii_letters
    NUMBERS = string.digits
    SYMBOLS = string.punctuation

    # Create list of all the possible characters
    CHARACTERS = LETTERS + NUMBERS + SYMBOLS

    # Set the random seed
    random.seed(randomSeed)

    # Generate the password by sampling all characters and return it
    password = ''.join(random.choices(CHARACTERS, k=passwordLength))
    return password

###############
# Main Method #
###############
if __name__ == '__main__':
    # Create an ArgumentParser class object for dealing with commandline args
    p = argparse.ArgumentParser(
        description="Generates a random password using letters (uppercase and lowercase), numbers, and symbols.")

    # Add an additional optional argument for the password length and random seed
    p.add_argument("-l", "--length", default=10, type=int,
                   help="Desired password length, 10 characters by deafult")
    p.add_argument("-r", "--randomSeed", default=None, type=int,
                   help="Desired random seed, None by deafult")

    # Read any commandline arguements sent to the program
    # NOTE: if -h or --help, the program stops here
    args = p.parse_args()

    # Generate and print the random password
    print(generatePassword(args.length, args.randomSeed))
```

## Math 

There are 52 possible letters (26 lowercase and 26 uppercase) and 10 digits that can be used in each password. That is a total of 62 characters. Characters can be repeated, which means there are ___ unique combinations for a password of lenth 10. The math is shown below:

$$x+y=10$$
