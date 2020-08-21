Bootstrap: docker
From: ubuntu:18.04

%labels
	CREATER Sheng
%post
	# Downloads the latest package lists (important).
    apt -y install software-properties-common
    add-apt-repository universe
    apt-get -y update
    # Runs apt-get while ensuring that there are no user prompts that would
    # cause the build process to hang.
    # python3-tk is required by matplotlib.
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
        python3 \
	    python3-distutils\
        python3-pip
    # Reduce the size of the image by deleting the package lists we downloaded,
    # which are useless now.
    rm -rf /var/lib/apt/lists/*
    # Install Python modules.
    pip3 install setuptools
    pip install numpy scipy glob pandas sklearn json pdb csv

%files
	SETTINGS.json
	features.py /
	model.py / 
	
%runscript
	python3 /features.py
	python3 /model.py
	
	
	