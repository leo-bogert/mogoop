mogoop
======

A script to dynamically create a temporary Hadoop cluster as a batch job to run on IBM Platform LSF.

Setup
=====

	git clone https://github.com/leo-bogert/mogoop.git
	cd mogoop
	wget http://www.eu.apache.org/dist/hadoop/common/stable/hadoop-1.2.1.tar.gz
	wget http://www.eu.apache.org/dist/hadoop/common/stable/hadoop-1.2.1.tar.gz.asc
	gpg --list-keys # initializes gpg in case you have not used it yet.
	gpg --recv-key 785436A782586B71829C67A04169AA27ECB31663
	gpg --verify hadoop-1.2.1.tar.gz.asc
	tar xzf hadoop-1.2.1.tar.gz
	ln -s hadoop-1.2.1/ hadoop

Execution
=========

You can obtain a Hadoop cluster which reserves all CPUs and all memory of 3 Mogon nodes via:

	./mogoop 3
	
Each node has 64 processors and 115 GB of RAM for your processing.