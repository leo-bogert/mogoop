mogoop
======

A script to dynamically create a temporary Hadoop cluster as a batch job to run on IBM Platform LSF.

Execution
=========

You can obtain a Hadoop cluster which reserves all CPUs and all memory of 3 Mogon nodes via:

	./mogoop 3

This will submit a batch job which:
- allocates the requested amount of nodes. Each node has 64 processors and 115 GB of RAM for your processing.
- Auto-configures Hadoop from scratch. You don't have to edit any config files!
- formats the HDFS on temporary local storage.
- opens a bash shell so you can use the cluster via the "hadoop" command.
- shuts down the cluster and erases it (including hdfs!) if you exit the shell via "exit".

You can prove that the cluster is working by entering the following into the shell:
	# List the contents of HDFS.
	hadoop fs -ls /
	# List currently running jobs.
	hadoop job -list

The file system and the job list will be pretty empty of course but the fact that the listings succeed proves that the cluster is fine.

Setup
=====
Execute the following on your Mogon shell. It will:
- Download Mogoop
- Download the Hadoop binaries from the official website and check their GPG signature
- Leave you in the directory "~/mogoop" where you can execute ./mogoop

	cd ~   # Please edit the "mogoop" script if you use a different directory!
	git clone https://github.com/leo-bogert/mogoop.git
	cd mogoop
	wget http://www.apache.org/dist/hadoop/common/hadoop-1.2.1/hadoop-1.2.1.tar.gz
	wget http://www.apache.org/dist/hadoop/common/hadoop-1.2.1/hadoop-1.2.1.tar.gz.asc
	gpg --list-keys    # initializes gpg in case you have not used it yet.
	gpg --recv-key 785436A782586B71829C67A04169AA27ECB31663
	gpg --verify hadoop-1.2.1.tar.gz.asc && tar xzf hadoop-1.2.1.tar.gz && ln -s hadoop-1.2.1/ hadoop
