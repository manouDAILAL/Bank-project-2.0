# Bank-project-2.0

This is the updated version of my previous bank program. Here's what changed:

- Instead of opening the file on every single operation, I now use vectors. The file is opened once when the program starts and once when it ends.
- I added a permissions system for users, using bitwise operations.
- The function calls are split up in a much more organized way, and I got rid of the giant function from the old version.
- I kept using loops to move between screens, so the stack doesn't fill up.

# Downsides

- In this design I gave up some security to get more speed, which is the opposite of the old version.
- The program can be improved a lot. More security layers and extra validation checks could be added, and it still has a few small flaws.
- I chose to skip those for now because this is a practice project before I start learning OOP.
