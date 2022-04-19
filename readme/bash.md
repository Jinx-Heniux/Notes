# Bash



```bash
#!/bin/bash
#
if [ $1 == '-s' ]; then
  ! grep "${2}$" /etc/shells &> /dev/null && echo "Invalid shell." && exit 7
elif [ $1 == '--help' ]; then
  echo "Usage: `basename $0` -s SHELL | --help"
  exit 0
else
  echo "Unknown Options."
  exit 8
fi

NumOfUser=`grep "${2}$" /etc/passwd | wc -l`
ShellUsers=`grep "${2}$" /etc/passwd | cut -d: -f1`
ShellUsers=`echo $ShellUsers | sed 's@[[:space:]]@,@g'`

echo -e "$2, $NumOfUser users, they are: \n$ShellUsers"

# 08 01 facl及用户及Linux终端
# https://www.youtube.com/watch?v=diGtbcD5U1g
```



## $RANDOM

```bash
#!/bin/bash
#
declare -i MAX=0
declare -i MIN=0

for I in {1..10}; do
  MYRAND=$RANDOM
  [ $I -eq 1 ] && MIN=$MYRAND
  if [ $I -le 9 ]; then
    echo -n "$MYRAND,"
  else
    echo "$MYRAND"
  fi
  [ $MYRAND -gt $MAX ] && MAX=$MYRAND
  [ $MYRAND -lt $MIN ] && MIN=$MYRAND
done

echo $MAX, $MIN

# 08 02 bash脚本编程之七 case语句及脚本选项进阶
# https://www.youtube.com/watch?v=jcKZFmvAXnE
```



## case

```bash
#!/bin/bash
#
case $1 in
[0-9])
  echo "digit";;
[a-z])
  echo "lower";;
[A-Z])
  echo "upper";;
*)
  echo "special character";;
esac

# 08 02 bash脚本编程之七 case语句及脚本选项进阶
# https://www.youtube.com/watch?v=jcKZFmvAXnE
```
