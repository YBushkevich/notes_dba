# 9. Основы написания bash-скриптов


### Внутренние переменные?

"$0" Containts the name, orthe path, of the script. This is now always
reliable

"$1" Positional Parameters contain the arguments that were passed to
the current script of function.

"$*" Expands to all the words of all the positional parameters. Double quoted,
it expands to a single string containin them all,

"$@" Expands to all the words of all the positional parameters. Double quoted,
it expands to a list of them as individual words.

$# Expands to the number of positional parameters that are currently set.

$? Expands to the exit code of te most recenlty completed foreground
command.

$$ Expands to the PID of the current shell.

$! Expands to the PID of the command most recently executed int the background

$_ Expands to the last argument of the last command that was executed

### Loops in bash

#### While loops 

    whiel [<some test>]; do
        <code>
    done

Example:

```bash
    counter=1
    while [ $counter -le 10]; do
        echo $counter
        (( $counter++ ))     
    done
```

#### Unti loops

    until [<some test>]; do
        <code>
    done

Example:

```bash
    counter=1
    until [ $counter -gt 10 ]; do 
        echo $counter
        (( counter++ ))
    done
```

### For loops

```bash
    
    for var in <list>; do
        <code>
    done
```

Example:

```bash
    names='alex mike bob'
    
    for name in $names; do
        echo $name
    done
```

### Select

```bash
    
    select var in <list>; do
        <code>
    done
```

Example:

```bash

    names='mike bob quit'

    select name in $names; do
        if [ $name == 'quit' ]
        then
            break
        fi
        echo $name
    done     
```







