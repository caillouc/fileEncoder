# FILE ENCODER 

This repository allows you to encode files using a password. 

## Install 

* First clone the repository 

* Then run the following command to install necessary packages.

```zsh
pip3 install ... 
```

* Once it is done, you first need to generate a salt. To do that, run the following command in the folder `fileEncoder` :

```zsh
python3 createSalt.py
```

* You will need to edit the top of `encoder.py` file by replacing this line : 

```python 
saltFileName = "/Volumes/SALT/.encoderFileSalt"
```

by : 

```python 
saltFileName = "/PATH/TO/YOUR/.encoderFileSalt"
```

>For more safety, you can move the file `.encoderFileSalt` to an external flash drive. Then you will need to plug in this external flash drive each time you need to encode/decode a file and replace the path accordingly (same step as above).


* Then, to use it easily with the terminal, copy this in your `.bashrc` or `.zshrc` file. You need to write the path to this project in `"PATH/TO/PROJECT"`.

```zsh 
# file encoder shortcut
encode(){
	DIR="`pwd`"
	builtin cd "PATH/TO/PROJECT"
	if [ -z "$1" ]; then 
		echo "invalid argument"
	else
		python3 encoder.py encode "$DIR/$1"
	fi
	builtin cd $DIR	
}

decode(){
	DIR="`pwd`"
	builtin cd "PATH/TO/PROJECT"
	if [ -z "$1" ]; then 
		echo "invalid argument"
	else 
		python3 encoder.py decode "$DIR/$1"
	fi
	builtin cd $DIR
}
```

## How to use it 

* To encode a file run this command in a terminal:

```zsh
encode PATH/TO/file
```

* To decode a file run this command in a terminal:
 
```zsh
decode PATH/TO/file
```