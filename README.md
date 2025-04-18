# CODESPACEDESKTOP #
In this repository, you will get a desktop using codespaces

#Install BIOS #
``wget -O bios64.bin "https://github.com/BlankOn/ovmf-blobs/raw/master/bios64.bin"``

#Download WIN8.1 LITE #
``wget -O win.iso "https://github.com/WhatTheBlock/WindowsSimplify/releases/download/iso/9600.20778_ML_230509.iso"``

#DOWNLOAD NGROK #
``wget -O ngrok.tgz "https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-amd64.tgz"``

#EXTRACT NGROK #
``tar -xf ngrok.tgz``

#SETUP NGROK #
``./ngrok authtoken <insert authtoken here>``

#START VNCSRV #
``./ngrok tcp 5900``

#INSTALL QEMU #

``sudo apt update``

``sudo apt install qemu-kvm -y``

#CREATE VM #

``qemu-img create -f raw win.img 32G``

``sudo qemu-system-x86_64 -m 12G -smp 4 -cpu host -boot order=c -drive file=win.iso,media=cdrom -drive file=win.img,format=raw -device usb-ehci,id=usb,bus=pci.0,addr=0x4 -device usb-tablet -vnc :0 -smp cores=4 -device e1000,netdev=n0 -netdev user,id=n0 -vga qxl -accel kvm -bios bios64.bin``
