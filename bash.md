Redirect stderr to file
```
command 2> file
```

Redirect stderr to stdout
```
command 2>&1
```

greps
```
grep -f FILE        # search patterns in FILE
grep -l             # return files with match (instead of lines)
grep -L             # return files without match (instead of lines)
```

sort chromosomes starting with chr
```
sort -k1,1V
```

Create numeric sequence (ex. for csvs with varying row lengths)
```
seq -s"," 1 100 > header
```

Delete range of jobs
```
qdel {111..115}
```

Add spaces (or other characters) between characters in a string:
```
sed 's/./& /g'
```

extract text between patterns
```
sed -n -e '/pattern1/,/pattern2/ p' file
```

add line to top of file
```
sed '1 i\TEXT' file > newfile
```

match pattern but dont replace entire pattern
```
sed 's/\([0-9]\.[0-9]\) /\1\t/'
# use () to create capture group, \1 to say keep capture group
```

Compress files
```
tar -czvf name.tar.gz dir/
```

Extract files
```
tar -xzvf name.tar.gz
```

Repeat character N x number of times
```
printf 'N%.0s' {1..x}
```

Concat files, but add line between each
```
for f in *.txt; do (cat "${f}"; echo) >> finalfile.txt; done
```

Change from lowercase to uppercase
```
tr '[:lower:]' '[:upper:]' < file > newfile
```

Delete newline
```
tr -d '\n' 
```

Replace multiple spaces with one comma:
```
sed 's/ \{1,\}/,/g' file
```

Add text to end of specific line (search for pattern before sub):
```
sed '/>/ s/$/NEWTEXT/'
```

Sort fastq file by read name:
```
cat file.fastq | paste - - - - | sort -k1,1 -t " " | tr "\t" "\n" > file_sorted.fastq
```

Get prefix and suffix from a string:
```
 b="${a%-*}"        # keeps whats before last -
 b="${a%%-*}"        # keeps whats before first -
 b="${a#*-}"        # keeps whats after first -
 b="${a##*-}"        # keeps whats after last -
```

Fail function to abort if situation not met:
```
fail() {
  echo "FAIL: $@" 1>&2
  exit 1
}
```

Check if previous command failed:
```
if [ $? -ne 0 ]; then echo "message"; fi
```

Calculate column average:
```
awk '{total += $COLUMNNUMBER; count ++} END {print total/count}' FILE.tsv
```

Split file into X number of files, and name subfiles with digits:
```
split -n l/10 -d FILE PREFIX
```

split string into X characters, one group per line:
```
echo STRING | egrep -o .{#}
```

make associative array and refer to it with a variable:
```
declare -A arrayname=(
[A]=x
[B]=y
)

name=$arrayname
for i in a b; do var=$name[$i]; echo ${!var}; done
```

read a file line by line:
```
while read l
do echo $l
done < file
```

assign variable names to each column in a file (expansion of above code):
```
while IFS="\t" read var1 var2 var3
do echo $var1 $var2 $var3
done < file.tsv
```

process substitution (code in the middle of different code):
```
cat file.txt <(head file2.txt)
```

here string (make string for bc to use):
```
bc <<< 5*4
```

echo a tab or recognize backslashes:
```
echo -e "hello\tworld"
```

subset prefix and suffix of string:
```
prefix=${string::10}    # first 10 characters
suffix=${string: -10}   # last 10 characters
```

sum list of numbers, one per line in file:
```
paste -s -d+ FILE | bc
```

get first few files in massive directory:
```
ls -U | head
```

add flags to bash script:
```
while getopts a:b:cd flags
do
    case "${flags}" in
        a) VAR1=${OPTARG};;
        b) VAR2=${OPTARG};;
        c) OPTIONAL_VAR1=${OPTARG};;
        d) OPTIONAL_VAR2=${OPTARG};;
    esac
done
```


Mount remote directory:
```
# Create new directory in home
mkdir /home/hgibling/dir

sudo nano /etc/fstab

# Add:
/path/to/dir /home/hgibling/dir fuse.sshfs defaults,allow_other,users,idmap=user,IdentityFile=/home/hgibling/.ssh/id_rsa2 0 0
```
https://wiki.archlinux.org/index.php/SSHFS#fstab_mounting_issues

Unmount stuck directory:
```
sudo diskutil umount force DIRNAME
```
