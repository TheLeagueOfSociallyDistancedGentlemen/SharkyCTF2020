# basic LSB
### 100 points

I intercepted an image in the communication of 2 sharkies from a shark gang. Those sharks knew I was listenning and they hidden a message in this image.

Do you think you can do something about it?

Creator: Fratso

Solution: 
Running zsteg pretty_cat.png gives the tantilizing "b1,rgb,lsb,xy       .. text: "Well done, you managed to use the classic LSB method. Now you know that there's nothing in the sea this fish would fear. Other fish run from bigger things. That's their instinct. But this fish doesn't run from anything. He doesn't fear. Here is your flag: " ", which is a riff on a line from Jaws.  Too bad the tool cuts off right where you want it to keep going.  I wonder...if they did that on purpose.

Rerunning zsteg with -E b1,rbg,lsb,xy gives the full flag with some other stuff.

Flag: 
shkCTF{Y0u_foUnD_m3_thr0ugH_LSB_6a5e99dfacf793e27a}
