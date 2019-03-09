#!/bin/bash

#directory to scan with find
scan=''	
#directory to which found files will be copied
dump=''
#put your find command here or else you will get an error 
myfind () { #find . ! -path . -print0 ; }

if [ ! -d "$dump" ]; then
	mkdir "$dump"	
fi
if [ ! -d "$scan" ] || [ ! -d "$dump" ]; then
	echo "Oops.  Did you enter valid scan and dump directories?" 1>&2
	exit
fi

working_dir="$(pwd)"
cd "$scan"		

while IFS="" read -r -d "" file <&4 ; do
	if [ -f "$file" ]; then
		echo "Found "$file""
		cp "$file" "$dump"   
	fi
done 4< <(myfind) 

cd "$working_dir"
