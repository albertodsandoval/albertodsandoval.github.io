---
title: "How to Download Manga and Upload to Kindle"
date: 2026-1-21
categories:
  - Blog
tags: 
  - Guide
  - Manga
---
# Step 1: Download HakuNeko
Download [HakuNeko](https://github.com/manga-download/hakuneko/releases/tag/v6.1.7). We will use HakuNeko to download manga files from different online sources. On mac, you may run into security issues which you can bypass like [this](https://support.apple.com/en-us/102445).

# Step 2: Adjust Settings in HakuNeko
Open HakuNeko and click the hamburger (3 horizontal lines) on the top left. From here you will be able to access settings. Make sure to change your Manga directory to where you want your manga to save on your computer. 

Also make sure your settings look like mine:\
![Image](/assets/images/Pasted image 20260121210457.png)\

# Step 3: Download Manga from HakuNeko
Follow the instructions from the right hand side of the HakuNeko desktop application to install manga.\
![Image](/assets/images/Pasted image 20260121221036.png)\

It is better to first search the web for sources that contain the manga you want, so you don't waste time waiting for HakuNeko to load. HakuNeko can take up to 10 minutes searching through the large libraries that the sources may offer, so it is definitely recommended to search online beforehand.

As for connectors (websites), I recommend these three:
* MangaDex
* MangaLife
* MangaFox

After searching for your manga in HakuNeko, make sure to filter the language to be only English, and then sort the manga by volume using this button:\
![Image](/assets/images/Pasted image 20260121222301.png)\

From here, you can download them all using the download button\
![Image](/assets/images/Pasted image 20260121222333.png)\
or manually download chapters by clicking on the cloud icon to the left of the chapter name.

They should all be saved in the location you specified in the setting. All chapters belonging to the same manga series will be stored in the same folder, which will be named whatever your manga series is named. 
# Step 4: Download Kindle Comic Converter
Head to the developer of [KCC's GitHub](https://github.com/ciromattia/kcc/releases) to download the latest release of KCC.

Look for **Assets** on the most recent version (v9.4.2 as of writing this), and click on it to see all of your options.

You want to download different files depending on what operating system you are running:
* **Windows:** KCC_\*.\*.\*.exe
* **Mac:** kcc_macos_arm_\*.\*.\*.dmg

# Step 5: Process Manga in KCC
After downloading KCC, go ahead and run the application. You may also have to bypass this app similar to HakuNeko if you are on Mac. 

If you are using a Kindle, which this tutorial is assuming you are, you have to download an additional tool to be able to convert to MOBI, which is ideal for Kindle readers. Download Kindle-Previewer [here](https://www.amazon.com/Kindle-Previewer/b?ie=UTF8&node=21381691011). You may run into the security issue *again* if you are on Mac.

Note: You don't actually have to *use* the Kindle-Previewer app, you just need to have it downloaded.

Once in KCC, make sure to select your eReader model. You can find the drop download *below* the **Add input file(s)** button. 

If you want the full manga *Right-to-left* experience, make sure to check that box. I would also select Cropping mode in order to remove margins. Especially if your reader has a smaller screen.

Now, select **Add input folder(s)** and find the folder for the series you want to convert. Then simply press **Convert**. After this, a file will be saved to the same folder that your manga files from HakuNeko were in.

# Step 6: Download Calibre (optional)
If you want to properly label your manga, and make it appear nice in your Kindle. If not, KCC developers suggest you can just plug your Kindle into your computer and drag the file generate by KCC into the Kindle documents folder. And you are now finished! Your manga should be ready to read on your Kindle.

If you want to go the Calibre route, download Calibre [here](https://calibre-ebook.com/download).

# Step 7: Using Calibre
Once you've installed Calibre, go ahead and open it up. On the top left, you will find the **Add books** button, click on that so we can add the manga to our Calibre library. After KCC has converted your manga, it may have been split up into multiple different parts. Go ahead and upload all parts to Calibre.

For each individual part, I would recommend cleaning up the Metadata. You can select all of the parts, right click, and then select Edit Metadata -> Edit Metadata in Bulk.

From here, you can change the Author, attribute a series, specify date published, etc. Up to you want info you want to have in your Kindle library. 

After that, you can *also* change the covers. I like to do this because manga have really neat covers, and I feel like I am missing out if the cover is just a random panel. To change covers, right click on one of the parts, select Edit metadata -> edit metadata individually. Now where it says **Change cover**, go ahead and click **Download cover**. This will search the internet for a bunch of cool covers for this manga. Download whichever one you like, and press OK at the bottom. Rinse and repeat for all the parts that you have.

Finally, plug in your reader to your computer. Now, you should be able to see a new button at the top that says **Send to device**. Select all of the manga you want to send over to your reader, and then click **Send to device**. After this is completed, you are all set! You officially downloaded manga onto your Kindle!
