# Install Wekan v0.32 on FreeBSD 11.0-RELEASE

## Prerequisites

Add user `wekan`

	# adduser

Install prerequisites packages

	# pkg install mongodb node4 npm2

Enable MongoDB

	# sysrc mongod_enable=YES
	# service mongod start

## Installation

As wekan

	$ cd
	$ fetch https://github.com/wekan/wekan/releases/download/v0.32/wekan-0.32.tar.gz
	$ tar -xzpf wekan-0.32.tar.gz

As root

	# chown -R wekan:wekan /home/wekan/bundle

As wekan

	$ cd ~/bundle/programs/server
	$ npm install
	$ npm install fibers

## First run

Considering that the default shell for a new user on FreeBSD is `/bin/sh`, the following ENV variables must be set according the following method before starting of Wekan. These must be adapted according the shell.

	$ MONGO_URL=mongodb://127.0.0.1:27017/wekan; export MONGO_URL
	$ ROOT_URL=https://example.com; export ROOT_URL
	$ MAIL_URL=smtp://user:pass@mailserver.example.com:25/; export MAIL_URL
	$ MAIL_FROM=wekan-admin@example.com; export MAIL_FROM
	$ PORT=8080; export PORT

Now it can be run

	$ cd ~/bundle
	$ node main.js
