# This manual describes how to modify MNE to do sleep scoring more conveniently and how to use it:dancers: .

Jiayi Liu, jiayiliu@pku.edu.cn, 2022/01/24



## :star:Setup Steps

### Step 1. Install Anaconda <https://www.anaconda.com/products/individual>

### Step 2. Create mne_sleep_scoring environment

### Step 3. Downloading .edf files which include PSG data <https://pan.baidu.com/s/1SJ1n2DY6psgwJbSjmXf2cA> (pwoc)

### Step 4. Downloading three .py scripts ./Scripts/ which modified by Jiayi Liu to make MNE more appropriate for sleep scoring and overwrite the original script in MNE.

\Anaconda_path\envs\mne_sleep_scoring\Lib\python3.9\site-packages\mne\viz\\\_mpl_figure.py

\Anaconda_path\envs\mne_sleep_scoring\Lib\python3.9\site-packages\\mne\viz\\utils.py

\Anaconda_path\envs\\mne_sleep_scoring\Lib\python3.9\site-packages\mne\annotations.py

**If you use Mac/Linux, please change '\\' to '/'**


## :star:How to use

### Step 1. Open Powershell (windows) or Terminal (Mac)

### Step 2. Switch to mne_ sleep_scoring environment ($ conda activate mne_sleep_scoring)

### Step 3. Run the following code in the terminal.

`import mne`

`file='I:\Data_daily\psg\s01.edf'`

`dataset=mne.io.read_raw_edf(file, preload=True)`

`dataset.filter(l_freq=0.3, h_freq=35, picks=['E1-M2', 'E2-M2', 'F3-M1', 'F4-M2', 'C3-M1', 'C4-M2', 'O1-M1', 'O2-M2'])`

`dataset.filter(l_freq=10, h_freq=100, picks=['Chin1-Chin2', 'Chin3-Chin2'])`

![image-20220124104016675](https://github.com/jiayiliu-pku/sleep_scoring_mne/blob/main/Figs/image-20220124104016675.png)

`dataset.plot(duration=30)`



### Step 4. Sleep scoring

#### If you want to score this frame as NREM 1, just press '1' and you will get one additional annotation figure.

![image-20220124104246216](https://github.com/jiayiliu-pku/sleep_scoring_mne/blob/main/Figs/image-20220124104246216.png)

#### Press '2' for NREM 2

#### Press '3' for NREM 3

#### Press 'w' for Wake

#### Press 'r' for REM

#### **After completing scoring of this file, you should close the annotation figure firstly and then close the plot figure.**



### Step5. Store your sleep scores

`dataset.annotations.save('test.csv',onset='relative')`

You will find the annotations including annotation information in the _test.csv_

![image-20220124112359931](https://github.com/jiayiliu-pku/sleep_scoring_mne/blob/main/Figs/image-20220124112359931.png)



# :clap: You have completed all steps. Congratulations!

