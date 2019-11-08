## GCH

Hacking into github contributions calendar.  
I wrote a script that pushes a commit to this directory everyday.

### Script Used
````python
import os
import datetime
import random

#cd to working directory
realdir = os.path.realpath(__file__).split('/github')[0]
os.chdir(f'{realdir}')

#checking if maintainer exists
if not os.path.exists('maintainer.txt'):
    with open('maintainer.txt', 'w') as f:
        f.write('First time')

def push_commits():
    if not os.path.exists('GCH'):
        os.system("git clone https://github.com/imneonizer/GCH.git")
        os.chdir('GCH')
        os.system("git config --global user.email 'mneonizer@gmail.com'")
        os.system("git config --global user.name 'Nitin Rai'")
    else:
        os.chdir('GCH')
        os.system(('git pull'))

    def repeat_commits():
        with open('realwork.txt', 'w') as f:
            f.write(str(datetime.datetime.now()))
            
        os.system(('git add .'))
        os.system(f"git commit -m 'Update'")

    ttc = int(input('Enter Number of commits: ')) #random.randint(1, 50)
    for i in range(ttc):
        repeat_commits()

    print(f'\ntotal commits: {ttc}\n')
    os.system('git push')

#checking if already pushed
with open('maintainer.txt', 'r') as f:
    date = f.readline()
    #date = '2019-11-08' #for force push
    if date == str(datetime.datetime.now().date()):
        print(f'{date}: already pushed')
    
    else:
        #pushing to github
        push_commits()

        #updating maintainer for pushed commit
        with open('maintainer.txt', 'w') as f:
            f.write(str(datetime.datetime.now().date()))
            print(f'push successful for: {str(datetime.datetime.now().date())}')
````

As soon i make this repository private or delete it, all those fake contribution marks on my profile will disappear.  
This is a fun project to try.
