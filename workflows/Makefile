#
# Example usage:
#
#  mkdir M100
#  cd M100
#  ln -s ....
#  make -f ../Makefile M100
#

help:
	@echo No help


# about 3 hours
M100:
	time casa --nogui -c ../example1.py   > example1.log  2>&1
	time casa --nogui -c ../workflow6a.py > example6a.log 2>&1
	time casa --nogui -c ../workflow6.py  > workflow6.log 2>&1

# about 10 mins and 4.5 GB
cloud197:
	time casa --nogui -c ../workflow1.py  > workflow1.log 2>&1

# 
skymodel:
	time casa --nogui -c ../workflow4.py  > workflow4.log 2>&1
