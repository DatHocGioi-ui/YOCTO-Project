I. Set-up
1.Install Host Packages

	 sudo apt-get install gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev pylint3 xterm python3-subunit mesa-common-dev zstd liblz4-tool
	 
2. Unzip yocto-project.tar và 

	cd yocto-project/YOCTOR_PROJECT/poky/

3. Initialize the Build Environment
	source oe-init-build-env
	
4. Update Your Local Configuration File

	vim /poky/build/conf/local.conf
	
   Anh chỉnh lại các biến DL_DIR, SSTATE_DIR, TMPDIR thành đường dẫn lần lượt của các thu mục downloads, sstate-cache, tmp trong file
local.conf
	
5. Start the build

	bitbake core-image-base
	
6. Flash the image to BBB and run

	cd tmp/deploy/images/beaglebone-yocto
	
   Delete all partition of the sd card. (Phải check xem of=/dev/sdb có phải là sdb hay là loại khác (ví dụ of=/dev/mmcblk0)
   	
   	sudo dd if=core-image-base-beaglebone-yocto.wic of=/dev/sdb bs=4M
