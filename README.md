### VehicleInsurance
  This project is aiming at validating pictures of accident spot for vehicle insurances. The service only accepts meaningful
  pictures while rejects the meaningless. It let uploading one know rejection reason with explanation to help them correct it.

  1. classify image into three group(that's, VIN,Vehicle,Else)
  2. detect a VIN(vehicle identification number)
  ![known](https://github.com/gustavkkk/VehicleInsurance/blob/master/vin.png)
  3. detect a vehicle
  4. detect a license plate(including a sloped)
  ![known](https://github.com/gustavkkk/VehicleInsurance/blob/master/lp.png)
  
### Setup & Run
    Setup
    Install Tesseract
    $ sudo apt-get install tesseract-ocr libtesseract-dev libleptonica-dev tesseract-ocr-all
    $ sudo pip install tesserocr
    Install Opnecv3
    $ cd ~
    $ wget -O opencv.zip https://github.com/Itseez/opencv/archive/3.4.0.zip
    $ unzip opencv.zip
    $ wget -O opencv_contrib.zip https://github.com/Itseez/opencv_contrib/archive/3.4.0.zip
    $ unzip opencv_contrib.zip
    $ cd ~
    $ wget https://bootstrap.pypa.io/get-pip.py
    $ sudo python get-pip.py
    $ sudo apt-get update
    $ sudo apt-get upgrade
    $ sudo apt-get install build-essential cmake pkg-config libjpeg8-dev libtiff5-dev libjasper-dev libpng12-dev libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libxvidcore-dev libx264-dev libgtk-3-dev libatlas-base-dev gfortran python2.7-dev python3.5-dev
    $ cd ~/opencv-3.1.0/
    $ mkdir build
    $ cd build
    $ cmake -D CMAKE_BUILD_TYPE=RELEASE \
        -D CMAKE_INSTALL_PREFIX=/usr/local \
        -D INSTALL_PYTHON_EXAMPLES=ON \
        -D INSTALL_C_EXAMPLES=OFF \
        -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-3.4.0/modules \
        -D PYTHON_EXECUTABLE=~/.virtualenvs/cv/bin/python \
        -D BUILD_EXAMPLES=ON ..
    $ make -j4
    $ make
    $ make clean
    $ sudo make install
    $ sudo ldconfig

    Install Python Packages
    $ git clone https://github.com/gustavkkk/VehicleInsurance
    $ cd VehicleInsurance
    $ sudo pip install -r requirements
    
    Run
    $ python webapp.py

### Download
  You can download [models & others](https://pan.baidu.com/s/1HRePvv0UVibMsXKxJOUs7g) from the following ulrs.
    
    url: https://pan.baidu.com/s/1HRePvv0UVibMsXKxJOUs7g
    password: jwyz
    
### Reference
  - [MicrocontrollersAndMore](https://github.com/MicrocontrollersAndMore/OpenCV_3_License_Plate_Recognition_Python)
  - [tesserocr](https://github.com/sirfz/tesserocr)
  
  
  
  ### Setup & Run
  
  - Preparing the aws server
	- Select AMI as Ubuntu Server 16.04 LTS (HVM), SSD Volume Type - ami-0565af6e282977273
	- Select Instance Type as m5ad.2xlarge
	-	Download pem file and change permission with chmod
chmod 400 deep_learning_test.pem
	-	Connect via ssh
ssh -i "deep_learning_test.pem" ec2-user@ec2-54-160-49-218.compute-1.amazonaws.com
	- Installation
	- Install necessary packages
sudo apt-get install tesseract-ocr libtesseract-dev libleptonica-dev tesseract-ocr-all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove x264 libx264-dev

sudo apt-get install build-essential checkinstall cmake pkg-config yasm
sudo apt-get install git gfortran
sudo apt-get install libjpeg8-dev libjasper-dev libpng12-dev

sudo apt-get install libtiff5-dev

sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev
sudo apt-get install libxine2-dev libv4l-dev
sudo apt-get install libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev
sudo apt-get install qt5-default libgtk2.0-dev libtbb-dev
sudo apt-get install libatlas-base-dev
sudo apt-get install libfaac-dev libmp3lame-dev libtheora-dev
sudo apt-get install libvorbis-dev libxvidcore-dev
sudo apt-get install libopencore-amrnb-dev libopencore-amrwb-dev
sudo apt-get install x264 v4l-utils

sudo apt-get install libprotobuf-dev protobuf-compiler
sudo apt-get install libgoogle-glog-dev libgflags-dev
sudo apt-get install libgphoto2-dev libeigen3-dev libhdf5-dev doxygen

sudo apt-get install python-dev python-pip python3-dev python3-pip
sudo -H pip2 install -U pip numpy
sudo -H pip3 install -U pip numpy
	- Reinstall cmake (Ubuntu 16 already installed cmake, but it doesn’t work well)
sudo apt-get remove cmake
sudo apt-get update
sudo apt-get install cmake
	- Prepare anaconda for python2.7 (we have to uninstall tiff because the ubuntu 16 only support tiff5.0 but opencv need tiff4.0)
conda remove libtiff
conda create --name py2 python=2.7
source activate py2
pip install opencv-python
pip install statistics
	- Download opencv and build it
cd ~
wget -O opencv.zip https://github.com/Itseez/opencv/archive/3.4.0.zip
unzip opencv.zip
wget -O opencv_contrib.zip https://github.com/Itseez/opencv_contrib/archive/3.4.0.zip
unzip opencv_contrib.zip
cd ~/opencv-3.4.0/
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D INSTALL_C_EXAMPLES=OFF \
    -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-3.4.0/modules \
    -D PYTHON_EXECUTABLE=/usr/bin/python \
    -D BUILD_EXAMPLES=ON ..
		make -j4
		sudo make install
		sudo ldconfig
	-	Clone the source code and build
git clone git@github.com:claimly/VehicleInsurance.git
cd VehicleInsurance
pip install -r requirements
mkdir uploads # 
	-	Run
python webapp.py
