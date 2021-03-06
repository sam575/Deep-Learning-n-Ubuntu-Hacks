# Deep-Learning-n-Ubuntu-Hacks

>For windows users: [Windows equivalent to Linux commands](http://www.covingtoninnovations.com/mc/winforunix.html)

>copying
```
scp -rCq Desktop/cs231n rakhil@xxx.xxx.xxx.xxx:Desktop/
rsync -avz -e 'ssh -i x.pem' Desktop/cs231n rakhil@xxx.xxx.xxx.xxx:Desktop/
rsync -avz Desktop/cs231n rakhil@xxx.xxx.xxx.xxx:Desktop/
```
#use rsync if you want to update files in the same directory

#if you want delete old files in the same directory use --delete

#add --rsync-path="sudo rsync" if ur copying to sudo location

#faster rsync
```
rsync -aqzP C3D rakhil@xxx.xxx.xxx.xxx:~/Desktop/
```
>tar
```
tar -xvzf dasd //extract
tar -cvzf dasd //compress
```

>ssh using pem file

#or use aliases in /etc/hosts and .ssh/config
```
ssh -i xxx.pem rakhil@xxx.xxx.xxx.xxx
```

>curr time
```
date
```

>root mode
```
sudo su
```

>appending file
```
echo 'dadaf3dad' >> lol.txt
```

>history of commands
```
history | grep "string"
vim ~/.bash_history
```
#reverse search with word

ctrl + r ; type string

>files n space in directory
```
du -hs #space in directory
find . -type f | wc -l #num files in directory
df -h #available space in disk
```
>list 
```
ls 
ll #advanced list 
ll -lrt #sort with time 
```

> Check quota alloted to user
```
quota -us
```

>ip
```
curl ipinfo.io/ip #global ip
ifconfig #get local ip
ipconfig #local ip forwindows
```

>going to D drive in windows.. no cd
```
D:
```

>vim

cursor to start: gg; end: G; end of line: $

del line: dd

del all: dG (from cursor to end)

search: /search_word ; n & shift + n or N for next and prev word 

>diff between files

#use meld in ubuntu or
```
vimdiff lol1.txt lol2.txt
```

>for viewing images
```
eog lol.jpg
```

>check symbolic links
```
ls -la /usr/bin/ | grep gcc
ll
```
>creating symbolic links
```
ln -sfn /usr/bin/gcc-4.3 /usr/bin/gcc
```

>env variables
```
printenv #list all
echo $LD_LIBRARY_PATH #print
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/rak/lib #add new path
```

>browser from terminal
```
sensible-browser
```
>wget
```
echo "check_certificate = off" >> ~/.wgetrc
```
>youtube-dl
```
youtube-dl -f best -f mp4 https://www.youtube.com/watch?v=ekyBklxwQMU --proxy xxx.xxx.xxx.xx:80 --no-check-certificate
# mp3 format
youtube-dl -x --audio-format mp3 -i --yes-playlist https://www.youtube.com/playlist?list=PLNPDZJ1Lllc9bIW77JV9JEotb7_FR40pZ
youtube-dl -x --audio-format mp3 -i PLNPDZJ1Lllc9bIW77JV9JEotb7_FR40pZ
```
>in sh file
```
#!/bin/bash #for bash script
#!/bin/sh #for shell script
```
#executing bash files
```
sh lol.sh 
```
#executing shell script
```
chmod +x lol.sh
./lol.sh 
```

>reading input from txt file in cpp
```
freopen("input.txt", "r", stdin);
```
>adding a user in ubuntu
```
sudo su
adduser username
usermod -aG sudo username #give sudo access
su - username #switch to new user
sudo ls -la /root #check if sudo access given
```

>search for string in all files
```
grep -r "lol"
grep -r "lol" . #in curr dir
grep -i "lol" #ignore-case
```
#search file 
```
locate lol.txt
```

## Python
>accessing n downloading files through browser
```
python -m SimpleHTTPServer 8080 #in remote server
xxx.xxx.xxx.xxx:8080 #open in local browser
```
>python libraries location

/usr/local/lib/python2.7/

>pip install locally
```
export PIP_CERT=/data/CRT_New.cer #if cert required
pip install lol --user
python -m pip install --user --upgrade lol
```
>using local library without installation
```
import sys
sys.path.insert(0,'/data/rakhil/keras')
```
>using linux commands
```
os.system('mkdir lol')
os.makedirs(lol, exist_ok=True)
```
>Try and expect
```
import traceback
try:
	# some error occurs
except Exception as e:
	print(traceback.format_exc())
```
## virtualenvwrapper
```
mkvirtualenv lol
workon lol
deactivate
rmvirtualenv lol
ls $WORKON_HOME
```
## Github
>pull
```
git status
git remote update
git pull
```
>push
```
git add -u #add only edited files
git add new_file.py #add a new specific file
git add . #add all files

git commit -m "lol"
git push -u origin master
```
>Git to overwrite local files
```
git fetch origin master
git reset —hard FETCH_HEAD
git clean -df
```
>Git pull only one file
```
git fetch
git checkout FETCH_HEAD lol.py
```
## tmux
```
tmux new -s name #create new tmux session
tmux attach -t name #attach a specific tmux session.. need not type full name, unique prefix is enough
tmux kill-session #in session or ctrl+d
```
detach: ctrl+b d

mouse up/down: ctrl+b `[`

next window: ctrl+b n prev: ctrl+b p

new window: ctrl+b c kill window: ctrl+b x

show tmux sessions in tmux: ctrl+b s

## GPU

>gpu info
```
lspci | grep VGA
```
>using gpu
```
#in terminal
echo $CUDA_VISIBLE_DEVICES
export CUDA_VISIBLE_DEVICES=1,2
#in python script
os.environ["CUDA_VISIBLE_DEVICES"] = "3"
```
>gpu usage with refresh interval 1s
```
nvidia-smi -l 1
```
>without filling terminal
```
watch -n 1 nvidia-smi
```
>user process running on GPU
```
ps -f `nvidia-smi | grep -A 100 PID | grep C | awk {'printf($3"\t")'}`
```
>cuda and cudnn versions
```
nvcc --version #cuda version
cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2 #cudnn version
```
## ipython
>ipython in remote machine and using it from local machine;go to browser localhost:8888
```
remote_user@remote_host$ ipython notebook --no-browser --port=8890
local_user@local_host$ ssh -N -L localhost:8888:localhost:8890 remote_user@xxx.xxx.xxx.xxx
```
>Common access system
```
ipython notebook --ip '*' --port 8890 --no-browser
```
>auto reload ipython
```
%load_ext autoreload
%autoreload 2
```
>for using system commands in ipython
```
!echo lol
```
>kill jupyter kernel from inside the notebook
```
%%javascript
Jupyter.notebook.session.delete();
```
## Keras 
```
vim ~/.keras/keras.json
```
```
THEANO_FLAGS=device=gpu0,lib.cnmem=0.55 python keras_proposal_layer.py #theano 
CUDA_VISIBLE_DEVICES=3 python train_rpn.py #tensorflow
```
## Caffe
#caffe suppress output prototxt https://stackoverflow.com/questions/29788075/setting-glog-minloglevel-1-to-prevent-output-in-shell-from-caffe

#use before import caffe
```
os.environ['GLOG_minloglevel'] = '2' 
```
## Tensorflow
>gpu memory control
```
config = tf.ConfigProto()
config.gpu_options.allow_growth = True #takes the min required memory or 
config.gpu_options.per_process_gpu_memory_fraction = 0.4 #fixed memory - 40% of total memory
session = tf.Session(config=config, ...)
```
>test gpu 
```
tf.test.is_gpu_available()
```
>saving and restoring tf model: 
http://cv-tricks.com/tensorflow-tutorial/save-restore-tensorflow-models-quick-complete-tutorial/

>tensorboard port forwarding on remote machine(6006) and viewing on local machine port(16006)
```
ssh -f -L localhost:16006:localhost:6006 <user@remote> #in local
ps aux | grep 6006 #for closing connection #in remote
kill -9 pid #in remote
```
## Octave
>
```
octave -q test.m 
```
or in octave command line: 
```
test
```
>installing locally
```
./configure --prefix=/home/maxpower/.octave38/
make -j2
make install
echo "alias octave38='~/.octave38/bin/octave'" >> ~/.bashrc
```
>uninstall
```
make uninstall
remove alias and downloaded folder
```
## ffmpeg
```
ffmpeg -i lolo.mp4 #print properties
ffmpeg -i inp.mp4 -ss 00:30:00 -t 00:50:00 -acodec copy -vcodec copy out.mp4 //cut video of 50 secs starting from 30s
ffmpeg -i 1.mp4 -i 2.mp4 -i 3.mp4 -filter_complex "[0:v] [0:a] [1:v] [1:a] [2:v] [2:a] concat=n=3:v=1:a=1 [v] [a]" -map "[v]" -map "[a]" output_3.mp4 #combine diff videos
ffmpeg -f concat -i mylist.txt -c copy output.mp4 #in list.txt format: file 'path/to/file'; combine similar videos
```
## Server 
>make socket connection
```
wscat -n -c wss://PRD_XXX.elb.amazonaws.com:443
```
>socket processes
```
netstat -tulpn #or
netstat -anp
ps -ef | grep 3000
sudo netstat -anp | grep :3000 | grep ESTABLISHED | wc -l
```
>>

```
forever list
```
## sytemctl
>Ref: https://wiki.archlinux.org/index.php/systemd
```
systemctl status nginx
systemctl start nginx
```
```
sudo cat /var/log/syslog | grep nginx #check logs
```
>enable service
```
sudo chmod 755 /etc/init.d/nginx 
sudo systemctl enable nginx
sudo systemctl daemon-reload
sudo systemctl reset-failed
```

> install sublime text 3 without sudo on ubuntu server
https://forum.sublimetext.com/t/install-sublime-text3-without-sudo/42893/4
