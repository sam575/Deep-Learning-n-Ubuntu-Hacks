# Deep-Learning-n-Ubuntu-Hacks

#copying<br/>
scp -rCq Desktop/cs231n rakhil@xxx.xxx.xxx.xxx:Desktop/<br/>
rsync -avz -e \'ssh -i x.pem\' Desktop/cs231n rakhil@xxx.xxx.xxx.xxx:Desktop/<br/>
rsync -avz Desktop/cs231n rakhil@xxx.xxx.xxx.xxx:Desktop/<br/>
#add --rsync-path="sudo rsync" if ur copying to sudo location<br/>
#faster rsync<br/>
rsync -aqzP C3D rakhil@xxx.xxx.xxx.xxx:~/Desktop/<br/>
<br/>
tar -xvzf dasd //extract<br/>
tar -cvzf dasd //compress<br/>
<br/>
#ssh using pem file<br/>
ssh -i xxx.pem rakhil@xxx.xxx.xxx.xxx<br/>
<br/>
#aliases in /etc/hosts and .ssh/config<br/>
<br/>
#curr time<br/>
date<br/>
<br/>
#root mode<br/>
sudo su<br/>
<br/>
#appending file<br/>
echo \'dadaf3dad\' >> lol.txt<br/>
<br/>
#history of commands<br/>
history | grep word<br/>
vim ~/.bash_history<br/>
#reverse search with word<br/>
ctrl + r ; type word<br/>
<br/>
#space in directory<br/>
du -hs<br/>
#num files in directory<br/>
find . -type f | wc -l<br/>
#available space in disk<br/>
df -h<br/>
<br/>
ls #list <br/>
ll #advanced list <br/>
ll -lrt #sort with time <br/>
<br/>
#get public ip<br/>
curl ipinfo.io/ip<br/>
#get local ip<br/>
ifconfig or ipconfig(windows)<br/>
<br/>
#going to D drive in windows.. no cd<br/>
D:<br/>
<br/>
#vim<br/>
cursor to start: gg; end: G; end of line: $<br/>
del line: dd<br/>
del all: dG(from cursor to end)<br/>
search: / ; n & shift + n or N <br/>
<br/>
#diff between files<br/>
vimdiff lol1.txt lol2.txt<br/>
use meld in ubuntu<br/>
<br/>
#for viewing images<br/>
eog lol.jpg<br/>
<br/>
#check symbolic links<br/>
ls -la /usr/bin/ | grep gcc<br/>
#creating symbolic links<br/>
ln -sfn /usr/bin/gcc-4.3 /usr/bin/gcc<br/>
<br/>
#env variables<br/>
printenv #list all<br/>
echo $LD_LIBRARY_PATH #print<br/>
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/rak/lib #add new path<br/>
<br/>
#browser from terminal<br/>
sensible-browser<br/>
<br/>
echo "check_certificate = off" >> ~/.wgetrc<br/>
<br/>
youtube-dl -f best -f mp4 https://www.youtube.com/watch?v=ekyBklxwQMU --proxy xxx.xxx.xxx.xx:80 --no-check-certificate<br/>
<br/>
#in sh file<br/>
#!/bin/bash<br/>
<br/>
#executing sh files<br/>
sh lol.sh <br/>
#or give permission<br/>
chmod +x lol.sh<br/>
./lol.sh <br/>
<br/>
#input txt file in cpp<br/>
freopen("input.txt", "r", stdin);<br/>
<br/>
#adding a user in ubuntu<br/>
sudo su<br/>
adduser username<br/>
usermod -aG sudo username #give sudo access<br/>
su - username #switch to new user<br/>
sudo ls -la /root #check if sudo access given<br/>
<br/>
#search for string in all files<br/>
grep -r "lol"<br/>
#search file <br/>
locate lol.txt<br/>
<br/>
<br/>

## Python<br/>

#accessing n downloading files through browser<br/>
python -m SimpleHTTPServer 8080 #in remote server<br/>
xxx.xxx.xxx.xxx:8080 #open in local browser<br/>
<br/>
#python libraries location<br/>
/usr/local/lib/python2.7/<br/>
<br/>
#pip install locally<br/>
pip install lol --user<br/>
python -m pip install --user --upgrade lol<br/>
export PIP_CERT=/data/CRT_New.cer<br/>
<br/>
#using local library without installation<br/>
import sys<br/>
sys.path.insert(0,\'/data/rakhil/keras\')<br/>
<br/>

## virtualenvwrapper<br/>

mkvirtualenv lol<br/>
workon lol<br/>
deactivate<br/>
rmvirtualenv lol<br/>
ls $WORKON_HOME<br/>
<br/>

## Github<br/>

#pull<br/>
git status<br/>
git remote update<br/>
git pull<br/>
#push<br/>
git add -u<br/>
git commit -m "lol"<br/>
git push -u origin master<br/>
<br/>

## tmux<br/>

tmux new -s name<br/>
tmux attach -t name<br/>
detach: ctrl+b d<br/>
mouse up/down: ctrl+b [<br/>
tmux kill-session //in session or ctrl+d<br/>
next window: ctrl+b n prev: ctrl+b p<br/>
new window: ctrl+b c kill window: ctrl+b x<br/>
show tmux sessions in tmux: ctrl+b s<br/>
<br/>

## GPU
#gpu info<br/>
lspci | grep VGA<br/>
<br/>
#using gpu<br/>
echo $CUDA_VISIBLE_DEVICES<br/>
export CUDA_VISIBLE_DEVICES=1,2<br/>
<br/>
#gpu usage with refresh interval 1s<br/>
nvidia-smi -l 1<br/>
#without filling terminal<br/>
watch -n 1 nvidia-smi<br/>
<br/>
nvcc --version #cuda version<br/>
cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2 #cudnn version<br/>
<br/>

## ipython<br/>

#ipython in remote machine and using it from local machine<br/>
remote_user@remote_host$ ipython notebook --no-browser --port=8889<br/>
local_user@local_host$ ssh -N -L localhost:8888:localhost:8889 rakhil@xxx.xxx.xxx.xxx<br/>
go to browser localhost:8888<br/>
<br/>
#auto reload ipython<br/>
%load_ext autoreload<br/>
%autoreload 2<br/>
<br/>
!echo lol #for using system commands in ipython<br/>
<br/>

## Keras <br/>

vim ~/.keras/keras.json<br/>
<br/>
THEANO_FLAGS=device=gpu0,lib.cnmem=0.55 python keras_proposal_layer.py #theano <br/>
<br/>
CUDA_VISIBLE_DEVICES=3 python train_rpn.py #tensorflow<br/>
<br/>

## Caffe<br/>

#caffe suppress output prototxt https://stackoverflow.com/questions/29788075/setting-glog-minloglevel-1-to-prevent-output-in-shell-from-caffe<br/>
#inc no less output .. use before import caffe<br/>
os.environ[\'GLOG_minloglevel\'] = \'2\' <br/>
<br/>

## Tensorflow<br/>

#gpu memory control<br/>
config = tf.ConfigProto()<br/>
config.gpu_options.allow_growth = True or config.gpu_options.per_process_gpu_memory_fraction = 0.4<br/>
session = tf.Session(config=config, ...)<br/>
<br/>
#test gpu <br/>
tf.test.is_gpu_available()<br/>
<br/>
#saving and restoring tf model<br/>
http://cv-tricks.com/tensorflow-tutorial/save-restore-tensorflow-models-quick-complete-tutorial/<br/>
<br/>
#tensorboard port forwarding on remote machine(6006) and viewing on local machine port(16006)<br/>
ssh -f -L localhost:16006:localhost:6006 <user@remote><br/>
ps aux | grep 6006 #for closing connection<br/>
kill -9 pid<br/>
<br/>

## Octave<br/>

octave -q test.m <br/>
or in octave command: test<br/>
<br/>
#installing locally<br/>
./configure --prefix=/home/maxpower/.octave38/<br/>
make -j2<br/>
make install<br/>
echo "alias octave38=\'~/.octave38/bin/octave\'" >> ~/.bashrc<br/>
#uninstall<br/>
make uninstall<br/>
remove alias and downloaded folder<br/>
<br/>

## ffmpeg<br/>

ffmpeg -i lolo.mp4 #print properties<br/>
ffmpeg -i inp.mp4 -ss 00:30:00 -t 00:50:00 -acodec copy -vcodec copy out.mp4 //cut video of 50 secs starting from 30s<br/>
ffmpeg -i 1.mp4 -i 2.mp4 -i 3.mp4 -filter_complex "[0:v] [0:a] [1:v] [1:a] [2:v] [2:a] concat=n=3:v=1:a=1 [v] [a]" -map "[v]" -map "[a]" output_3.mp4 #combine diff videos<br/>
ffmpeg -f concat -i mylist.txt -c copy output.mp4 #in list.txt format: file \'path/to/file\'; combine similar videos<br/>
<br/>

## Server <br/>

#make socket connection<br/>
wscat -n -c wss://PRD_XXX.elb.amazonaws.com:443<br/>
<br/>
#socket processes<br/>
netstat -tulpn <br/>
ps -ef | grep 3000<br/>
sudo netstat -anp | grep :3000 | grep ESTABLISHED | wc -l<br/>
<br/>
forever list<br/>
<br/>

## sytemctl <br/>

systemctl status nginx<br/>
systemctl start nginx<br/>
<br/>
sudo cat /var/log/syslog | grep nginx #check logs<br/>
<br/>
#enable service<br/>
sudo chmod 755 /etc/init.d/nginx <br/>
sudo systemctl enable nginx<br/>
sudo systemctl daemon-reload<br/>
sudo systemctl reset-failed
