'''
Created on 2016-9-29

@author: linsheng
'''
import time
import os
from subprocess import PIPE, Popen
def cmdline(command):
    process = Popen(
        args=command,
        stdout=PIPE,
        shell=True
    )
    return process.communicate()[0]

def getduration(path):
    # ffprobe -i panasonic_tokyo.mp4 -show_format -v quiet | grep duration
    cmd ='ffprobe -i "%s" -show_format -v quiet | findstr duration' %(path)
    print cmd
    var = cmdline(cmd)
    print var
    print int(float(var.split('=')[-1]))
    return int(float(var.split('=')[-1]))

def cutup_time():
#     thispath=os.getcwd()
    thispath="E:/video_02_ok/fengjing/crop"
    pathpath="E:/video_02_ok/fengjing/crop/crop"+"/"
    for rt, dirs, files in os.walk(thispath):
        for i in files:
            if i.endswith(".mp4"):
                
                os.makedirs("E:/video_02_ok/fengjing/crop/crop"+"/"+i)
                step =15
                paththis=thispath+"/"+i
                duration = getduration(paththis)
                print duration
                y=0
                for ii in range(5,duration,15):
                    pathpaths = pathpath +str(i)+"/"+str(i)+str(y)+".mp4"
                    print pathpaths
#                     cmd="ffmpeg -y -i " + paththis + " -ss " + str(i) + " -t " + str(step) + " " + ""
                    cmd ='ffmpeg -y -i "%s" -ss %s -t  %s  "%s" ' %(paththis,str(ii),str(step),pathpaths)
                    print cmd
                    os.system(cmd)
                    y+=1
                    
                
    


if __name__ == "__main__":
    start_time = time.time()
    cutup_time()
    print("--- %s seconds ---" % (time.time() - start_time))
