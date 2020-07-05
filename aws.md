# AWS - EC2 - Instance Set-Up

## Instance Creation

1) Navigate to EC2 Instances Console within AWS (signed in)
2) Select appropriate data centre 
	- Sparta Academy = Ireland
3) Launch Instance
4) Choose Amazon Machine Image
	- Ubuntu Server 16.04 LTS
5) Choose Instance Type
	- Take only what you need - CPUs, Memory etc
6) Configure Instance
	- Network, role, shutdown behaviours etc
	- NORMALLY: Protect against accidental termination
	- Number of instances (machines) [1]
	- Network
	- Subnet (physically isolated availability zones) [1b, 251 IPs available]
	- Auto-assign Public IP [Yes]
7) Add Storage
	- Connect hard drives
	- Take only what you need [8GB]
8) Add Tags
	- Naming.Convention.Is.Important
	- Key:Value
	-[Name:Eng57.Patrick.C.NodeJSSampleWebApp]
9) Configure Security Group
	- Create New:
		- Name [Eng.57.Patrick.C.HomeAccess]
		- Description [Home access for Patrick C. on diff ports]
		- Type, Protocol, Port Range, Source, Description
		- [SSH, TCP, 22, MY IP, 'Patrick IP port 22 access']
		- [Custom, TCP, 3000, MY IP, 'Patrick IP port 3000 access']
		- [Custom, TCP, 5000, MY IP, 'Patrick IP port 5000 access']
		- [Custom, TCP, 80, MY IP, 'Patrick IP port 80 access']
		- [HTTPS, TCP, 443, MY IP, 'Patrick IP port 443 access']
10) Review
	- Check everything
11) Choose key pair
	- Create New
		- [Eng57.Patrick.C]
		- Generates SSH key in Downloads,
		- `$ mv Eng57.Patrick.C.pem ~/.ssh`
	- Choose Class key
12) Launch!

## Machine Set Up

1) Sending in bash script:
	- `environment/app/provision.sh`
	- Permissions! `-rwxr-xr-x` <-- What we want
	- Convert to unix:
		- `$ dos2unix provision.sh`
	- `$ scp -i ~/.ssh/Eng57PatrickC.pem provision.sh ubuntu@[IPv4 Public IP]:/home/ubuntu`
		- [secure copy in] [key] [file] [id@ip:path]
2) Getting in:
	- `$ ssh -i  ~/.ssh/Eng57PatrickC.pen ubuntu@[IPv4 Public IP]`
		- [ssh in] [key] [id@ip]
3) Running provision
	- `~$ ./provision.sh`
4) Sending in `app/`
	- `scp -i ~/.ssh/Eng57PatrickC.pem -r app/ ubuntu@[IPv4 Public IP]:/home/ubuntu/app`
	- Takes a while

- scp
- rsync

## Start App

1) ssh in, FROM `~/.ssh`
	- `$ ssh -i Eng57PatrickC.pem ubuntu@[IPv4 Public IP]`
2) `$ cd ~/app`
   EITHER
   `npm install`
   `npm start`
   OR
   `pm2 start app.js`  <--- preferable
3) Navigate to app
	- (AWS) IPv4 Public IPIP:3000