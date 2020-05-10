# Erwins File Manager

### 200 Points

### Challenge:

Erwin just built himself a website. He is talking about quantum information science but in the end he doesn't know much about infosec. Could you help him fulfill his goal by reapplying quantum concept on this website ?

Creator: MasterFox

http://erwin.sharkyctf.xyz

@app.route('/upload', methods=["POST"])
def get_file():
	# Wenn die Anfrage eine Datei enthält
	if 'file' in request.files:
		new_file = request.files["file"]
		filename = save_file(new_file)

		# Überprüfen Sie das Dateiformat
		is_ELF = check_ELF(filename)
		is_PDF = check_PDF(filename)
		is_JAR = check_JAR(filename)
		is_JPG = check_JPG(filename)

		if is_ELF and is_JAR and is_PDF:
			put_aside(filename)
			return upload(msg=SECOND_PART_OF_FLAG)
		elif is_ELF and is_JAR:
			put_aside(filename)
			return upload(msg=FIRST_PART_OF_FLAG)
		elif is_JPG and is_JAR:
			put_aside(filename)
			return upload(msg=THIRD_PART_OF_FLAG)
		else:
			# Datei löschen
			remove(filename)
			return upload(error="Bad file")
	else:
		return upload(msg="No file detected")

### Solution:
The site has a snippet of code showing high level logic around what impossible combination of file types will give flags.  One file that's both a JPG and a JAR.  Those calls for check_PDF didn't appear to be from any standard Python library, though I'm not that great at Python.  There are a LOT of reference to Erwin Schrodinger except for what he's most known for, his quantum mechanic's thought experiment about a cat in a box.  So cat the files together and upload them for each flag portion and you get....

"shkCTF{Schr0diNgeR_" and
"_w4s_A_gRea7" and
"_p01yg1o7_4e78011325dfbe4a05fd533ea422cc94}"


### Flag:
shkCTF{Schr0diNgeR_w4s_A_gRea7_p01yg1o7_4e78011325dfbe4a05fd533ea422cc94}


# My huge file
### 298 Points
I have a very big file for you. I hid a present inside.

Classic tools wont be useful here.

Connect with ssh big@sharkyctf.xyz -p 9000. Password : big.

Creator : Nofix

### Solution:

I REALLY overthought this.  I'm starting to pick up on a patern there.  So first....the hint is BULLSHIT.  I used the most classicist of tools.  One I use nearly every day.  Well not as much since I started working for a company that ingests logs, but I digress.

First...don't bother cat'ing the file, its too big. xxd, strings, and a bunch more are disabled.  If you run sed it gets killed after a few seconds.  First off I ran tr and tried to kill all the white space and write a file to the /tmp folder, which they gave us.  That didn't seem to shring anything.  They left Python enabled so I wrote my own quick script to display the hex to see how this 15tb file is padded.  Looks like mostly Null, which explains why my tr command that removed whitespace didn't do much.  First I updated the python to strip Null and write to a file.  Waaaaay too slow.  Back to tr...still waaaaay too slow.

Then I thought...I wonder what's at the end of the file.  "tail -n 100 my_huge_file"  Nope, that hung and just kept chewing on the file.  That's wierd...I wonder what its stuck on?  Oh...I bet its trying to figure out how to count backwards by lines and since the file is basically ALL null.  I wonder if I can just tail by bytes.  Yup.  "tail -c 100 my_huge_file" and it spat out the flag.  Lots of swearing ensued.

I messaged the challenge author after and this was definitely not the intended way to solve it, which makes me even happier that it worked. (:


### Flag:
shkCTF{sp4rs3_f1l3s_4r3_c001_6cf61f47f6273dfa225ee3366eacb8eb}
