## Gen711/811 Practical Exam 2023

## NAME: Riley Wilson

__INSTRUCTIONS__
1. DO NOT USE COMMANDS OR SYNTAX WE HAVE NOT COVERED IN LAB UNLESS OTHERWISE SPECIFIED. Everything that you need to complete this exam has been covered in the lab sections, and can be found in the presentations. If you really want to use outside resources, please provide the reason you use it and what it does. 
   - For example, If I use `grep "^>" file.txt`, I must specify that the "^" character matches the front of the line and I used it to specify fasta header lines always start with ">".

2.  Write the command below each question. If the question specifies to add any other information, provide that below the command you used to generate the answer
    - For example, If the question is "Find how many words are in a file, give the command and number of words", my answer could be 
        ```
        wc -w example_file.txt
        15
        ```

__HELPFUL INFO__  
- Do not spend too much time on a single prompt. It's important to get to all prompts.    
- If you get stuck and do not know how to proceed: specifically ask for the answer.  
- Help will get you to the next step, but you will lose points for that prompt.
- Questions on clarification of the question does not result in the loss of points. 

## Practical Start

### Part 1: single commands (20 points total)
__All commands here won't require piping, but may involve using multiple commands in a row__

#### 1. Paste the command(s) below that you used to get the practical into your home directory (2 points)
	cp /tmp/REAL_PRACTICAL.md ~
#### 2. Make a new directory labeled `practical` in your home directory, and another directory labeled `sequences` within `practical`. Do this in one command. (2 points)
	mkdir -p ~/practical/sequences
#### 3. Move into the `sequences` directory. (1 point)
	cd ~/practical/sequences
#### 4. Provide the absolute path to the `sequences` directory, along with the command used to generate it. (2 point)
	/home/users/rmw1063/practical/sequences
#### 5. Copy all fasta files from within the `/tmp/practical` to your `sequences` directory while leaving all other file types behind. Do this in one command. (2 points)
	cp -r /tmp/practical *.fasta ~/practical/sequences
#### 6. Copy everything from `/tmp/practical` into your `practical` directory (including the fasta files). Delete just the fasta files while keeping everything else. Do this in just 2 commands, one for each step. (2 points)
	cp -r /tmp/practical ~/practical
#### 7. Concatenate the files within `practical` into one file called `items.txt`. (2 points)
	cat *.txt > items.txt
#### 8. Create your own file titled `colors.txt`. Add 3 colors within the file in the same format as the other text files. Give the command or describe your process of adding to the file. (3 points)
	touch colors.txt
	nano colors.txt (added pink, purple, and orange)
#### 9. Add the items in your `colors.txt` to the end of `items.txt`. (2 points)
	cat colors.txt >> items.txt
#### 10. How many total items are within `items.txt`? Give the count and command used to generate the count. (2 points)
	wc -l items.txt
	15 items
### Part 2: Piped commands (20 points total)
__All commands used here will involve piping of some sort__

#### 11. Provide a list of unique items within the `items.txt` file. Also provide the command used to generate the list. (5 points)
	bat 
	blueberry
	carrot
	human
	kale
	orange
	pear
	pink
	potato
	purple
	turtle
	watermelon
	sort items.txt | uniq
#### 12. In the `sequences` directory, count how many sequences are within all fasta files. Provide the command and count below. (5 points)
	cat *.fasta | grep -o ">" | wc -l
	399 sequences
#### 13. Create a file named `accession_numbers.txt` that stores the sequence accession number from all headers of all fasta files. Please only store the sequence accession number at the beginning, not the descriptions afterward. Provide the command used to generate the file. (5 points)
- For example, a header of `>NC_080634.1 Ammospiza nelsoni isolate bAmmNel1 chromosome 2, bAmmNel1.pri, whole genome shotgun sequence`, should be stored as `>NC_080634.1`.
	grep -o ">" *.fasta | cut -d " " -f1 *.fasta > accession_number.txt
#### 14. List the first 8 commands within `/bin` that contain two repeated p's in a row (`pp`) within their name. Provide the list and the command used to generate the list below (5 points)
	411toppm
	apport-bug
	apport-cli
	apport-collect
	apport-unpack
	appres
	bmptoppm
	check-language-support
	ls /bin | grep "pp" | head -n 8
### Part 3: Command Comprehension (10 points total)
__You will be given a command. Please describe what the command will do. You do not have to run these commands yourself, but if it is helpful to you, you can try to replicate them in your own terminal.__

#### 15. `seq 1 10` Provide a short description, and how you found it. (HINT: You have not seen this command before. How would you find out what it does using your terminal?) (2.5 points)
	This command lists out numbers 1 through 10 in numerical order. 
#### 16. `ls -lh /home | grep "unh"` (2.5 points)
	This command will list in human-readable form everything in the home directory that contains the letters "unh" in the file/directory name 
#### 17. `grep "@SRR" *.fastq | sort | uniq | wc -l` (2.5 points)
	This command pulls all of the headers from all the fastq files in the directory, sorts them alphabetically, removes any duplicate lines, and then tells you the number of lines piped. 
#### 18. `cat file.something | tail -n 5 | head -n 1` (2.5 points)
	This command opens "file.something", only focusing on the last 5 lines initially but then prints the first line only of those last five lines.
### Once you complete the practical, please download it to your local computer and upload it to canvas to be graded
