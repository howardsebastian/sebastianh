## Lab 02

- Name:Sebastian Howard
- Email: howard.520@wright.edu

Instructions for this lab: https://pattonsgirl.github.io/CEG2350/Labs/Lab02/Instructions.html

## Part 1 Answers

Full / absolute path to your private key file: /home/ubuntu/vocky.pem

Command to SSH to AWS instance:
```
ssh -i /home/ubuntu/vockey.pem ubuntu@<your-public-ip>
```

## Part 2 Answers

1. `chmod u+r bubbles.txt`
    - Means: GIve the user read permission
    - Assessment: correnct if user can read it 
2. `chmod u=rw,g-w,o-x banana.cabana`
    - Means: User gets read/write; group loses write; others lose execute
    - Assessment:Correct if the goal is to restrict group/others while giving owner full control.
3. `chmod a=w snow.md`
    - Means: Everyone (user, group, others) gets write only.
    - Assessment: Risky — removes read/execute for all. File becomes write‑only, which is unusual
4. `chmod 751 program`
    - Means: User = rwx (7), group = r-x (5), others = --x (1)
    - Assessment:Correct for a program where only the owner can modify, group can run/read, others can only run.
5. `chmod -R ug+w share`
    - Means: Recursively give user & group write permission on  and all contents.
    - Assessment:Assessment: Correct for shared editing inside the directory.


## Part 3 Answers

1. Command to create new user: sudo adduser BOB
2. Path to new user's home directory: /home/BOB
3. Evaluate if `ubuntu` can add files to new user's home directory: NO
4. Command to switch to new user:su BOB
5. Command(s) to go to new user's home directory:cd/home/BOB
6. Evaluate if new user can add files to user's home directory:NO
7. Command to return to `ubuntu` user: exit 
8. Command to return to `ubuntu` home directory: cd

## Part 4 Answers

1. Command(s) to create group named `squad` and add members:sudo groupadd squad
sudo usermod -aG squad BOB
2. Command(s) to add `ubuntu` & user to group `squad`:sudo usermod -aG squad ubuntu
sudo usermod -aG squad BOB
3. Command(s) to allow `squad` to view the `ubuntu` user's home directory contents:sudo chmod g+rx /home/ubuntu
4. Command(s) to modify `share` to have group ownership of `squad`:sudo chgrp squad share
sudo chmod g+rwx share
5. Describe your tests and commands with the user account: logged in as bob(su bob), Attempted to  before permissions → failed, After adding group permissions → succeeded
6. Describe the full set of permissions / settings that enable the user to make edits:share owned by group squad, Group has rwx permissions, User added to squad, Directory permissions allow traversal (x) and writing (w)


## Part 5 Answers

For each, write the command used or answer the question posed.

1. Command(s) to make file using `sudo`: sudo touch madewithsudo.txt
2. Command(s) to make file with `root`:sudo -i, touuch madewithsudo.txt, exit
3. Describe / compare ownership and permissions of files:
4. Which account can do what actions? (Type Y or N in columns)

Contents inside of `share`
| Account   | Can View  | Can Edit  | Can Change Permissions    |
| ---       | ---       | ---       | ---                       |
| `root`    |  y         |   y        |         y                  |
| `ubuntu`  |    y       |    y       |         n                  |
| `BOB`     |    y       |    y       |          n                 |

`madewithsudo.txt`
| Account   | Can View  | Can Edit  | Can Change Permissions    |
| ---       | ---       | ---       | ---                       |
| `root`    |    y       |    y       |       y                    |
| `ubuntu`  |    y       |    n       |       n                    |
| `BOB`     |    y       |    n       |       n                    |

5. Command(s) to modify permissions:sudo chmod 664 madewithsudo.txt, sudo chmod g+w share
6. How to give user account `sudo`:sudo usermod -aG sudo BOB

## Part 6 - Citations / Resources

- Linux permissions:
https://man7.org/linux/man-pages/man1/chmod.1.html (man7.org in Bing) — Used to confirm permission meanings.
- User & group management:
https://man7.org/linux/man-pages/man8/useradd.8.html (man7.org in Bing) — Helped verify user creation commands.
https://man7.org/linux/man-pages/man8/groupadd.8.html (man7.org in Bing) — Used for group creation syntax.
- SSH usage:
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html (docs.aws.amazon.com in Bing) — Used for SSH command format.


## Citations

To add citations, provide the site and a summary of what it assisted you with.  If generative AI was used, include which generative AI system was used and what prompt(s) you fed it.
