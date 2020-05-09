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
