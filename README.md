# get-audience-feedback

This demo shows how to capture audience feedback using a QR code and process the request using Node-RED. A random message is  created acknowledging the feedback and returned to the invoker and as new tweet on Twitter.

## Prerequisites
None

## Steps to deploy Node-RED on Bluemix

**Step 1:** If you don't already have a Bluemix account, go to [http://www.bluemix.net] (http://www.bluemix.net) and sign up (it's free).

**Step 2:** Log into your bluemix account.

**Step 3:** Navigate to the Bluemix catalog.

**Step 4:** Click on the "Node-RED Starter" tile. It's in the B"mapoilerplate" section towards the top of the catalog.

**Step 5:** Enter a unique name for your application into the "Name:" field on the right hand side.

**Step 6:** Click "create" to deploy the application on Bluemix.

**Step 7:** After a minute or two, you should see a notice that your application is now running. Click on the blue link at the top, it should be named something like: http://TheNameThatYouChoseInStep5.mybluemix.net .

**Step 8:** The above should lead you to a page with the title "Node-RED in Bluemi"x. It has a big red button "Go to your Node-RED flow editor" on the right. Click on it.

**Step 9:** You are now be in your Node-RED flow editor.

## Steps to import the Node-RED flow
**Step 10:** Here is the flow that will process the audience feedback. Select all of the JSON below and copy it into your clipboard.

```
[{"id":"a26ac3f9.1d12e8","type":"http in","name":"positive feedback","url":"/yup","method":"get","swaggerDoc":"","x":308,"y":291,"z":"710b37a5.df17d8","wires":[["d1fa4292.7da448"]]},{"id":"37ea13df.1edf7c","type":"http response","name":"return web answer","x":843,"y":249,"z":"710b37a5.df17d8","wires":[]},{"id":"78a362ca.e5ebc4","type":"twitter out","twitter":"","name":"Tweet","x":804,"y":361,"z":"710b37a5.df17d8","wires":[]},{"id":"d1fa4292.7da448","type":"function","name":"positive feedback","func":"var conference=\"#coffeeWorld\";\nvar tstamp=(new Date).toISOString().replace(/t/gi,' ').trim();\n\nvar messages = [\n\t\"great session\",\n\t\"auf den Punkt\",\n\t\"viel gelernt\",\n\t\"great & interactive demo\",\n\t\"guter Vortrag, jetzt ein #Bier\"\n];\n\t\nvar hashtags1 = [\n\t\"#ibmbluemix\",\n\t\"#softlayer\",\n\t\"#paas\",\n\t\"#bluemix\",\n\t\"#ibmcloud\",\n\t\"#cloud\"\n];\n\t\nvar hashtags2 = [\n\t\"#twitter\",\n\t\"#integration\",\n\t\"#nodered\",\n\t\"#demo\",\n\t\"#iot\"\n];\n\t\nvar message = messages[Math.floor(Math.random() * messages.length)];\nvar hashtag1 = hashtags1[Math.floor(Math.random() * hashtags1.length)];\nvar hashtag2 = hashtags2[Math.floor(Math.random() * hashtags2.length)];\n\t\nmsg.payload=\"@data_henrik received positive feedback at \"\n +conference+\" '\"+message+\"' \"+hashtag1+\" \"+hashtag2+\" \"+tstamp;\n\nreturn msg;","outputs":1,"noerr":0,"x":545,"y":291,"z":"710b37a5.df17d8","wires":[["37ea13df.1edf7c","78a362ca.e5ebc4","f652c2cf.7788d"]]},{"id":"e6b60a72.43932","type":"http in","name":"mixed feedback","url":"/boo","method":"get","swaggerDoc":"","x":323,"y":450,"z":"710b37a5.df17d8","wires":[["2d2578a5.231478"]]},{"id":"2d2578a5.231478","type":"function","name":"mixed feedback","func":"var conference=\"#coffeWorld\";\nvar tstamp=(new Date).toISOString().replace(/t/gi,' ').trim();\n\nvar messages = [\n\t\"an OK session\",\n\t\"selbst meine Oma weiß mehr über die Cloud\",\n\t\"not what I expected\",\n\t\"well, COULD have been a good presentations\",\n\t\"#Bier vorher und Vortrag wäre gut geworden\"\n];\n\t\nvar hashtags1 = [\n\t\"#ibmbluemix\",\n\t\"#softlayer\",\n\t\"#paas\",\n\t\"#bluemix\",\n\t\"#ibmcloud\",\n\t\"#ibm\",\n\t\"#cloud\"\n];\n\t\nvar hashtags2 = [\n\t\"#demo\",\n\t\"#integration\",\n\t\"#nodered\",\n\t\"#enterprise\",\n\t\"#demo\",\n\t\"#iot\"\n];\n\t\nvar message = messages[Math.floor(Math.random() * messages.length)];\nvar hashtag1 = hashtags1[Math.floor(Math.random() * hashtags1.length)];\nvar hashtag2 = hashtags2[Math.floor(Math.random() * hashtags2.length)];\n\t\nmsg.payload=\"@data_henrik received mixed feedback at \"\n +conference+\" '\"+message+\"' \"+hashtag1+\" \"+hashtag2+\" \"+tstamp;\n\nreturn msg;","outputs":1,"noerr":0,"x":564,"y":447,"z":"710b37a5.df17d8","wires":[["78a362ca.e5ebc4","af68311.c747a5","45946be9.9775dc"]]},{"id":"f652c2cf.7788d","type":"debug","name":"Debugging","active":false,"console":"false","complete":"payload","x":819,"y":194,"z":"710b37a5.df17d8","wires":[]},{"id":"af68311.c747a5","type":"http response","name":"return web answer","x":840,"y":474,"z":"710b37a5.df17d8","wires":[]},{"id":"45946be9.9775dc","type":"debug","name":"Debugging","active":false,"console":"false","complete":"payload","x":815,"y":526,"z":"710b37a5.df17d8","wires":[]}]
```
**Step 11:** Next import the flow into the Node-RED instance on Bluemix.

- Click on the menu on the upper right of the Node-RED user interface

- Navigate to "Import" and then "Clipboard"

- Paste the content of your clipboard (which should contain the flow that you copied in step 10 above) into the window and click on "Ok"

**Step 12:** You should now see the imported flow in your Node-RED editor.


## Steps to configure your Node-RED flow
tbd

## Steps to generate QR Code and set up feedback HTML page
tbd

# License

See [LICENSE](LICENSE) file.
