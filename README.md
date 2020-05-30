# OPC2MongoDB

This tool allows to connect to OPC UA and DA servers, poll for data and subscribe to events and write data in real time to a MongoDB database.

It is simple to configure, the opc2mongodb.conf file is self explained, it must be put in the same folder as the exe file.

The code is written in C# and it uses a forked h-OPC and the oficial MongoDB libraries for C#.

Requires https://github.com/riclolsen/h-opc.

Requires the .NET fremework 4.6 or later.

Executable binaries are available for download in the Releases section.

Need any help? Create an issue here or contact me.
Here is my LinkedIn contact: https://www.linkedin.com/in/ricardo-olsen/.

Example of config file:

	#mongoURL user      passwd ip        port  database
	mongodb://mongouser:secret@127.0.0.1:27017/opc2mongodb
	# use as below for unauthenticated local database server
	# mongodb://127.0.0.1:27017/opc2mongodb
	
	# OPC SERVERS

	#  OPC_UA_URL,                   READ_INTERVAL_IN_SECONDS,  SERVER_ID=MONGO_COLLECTION_NAME, CERTIFICATE_FILE_PATH, CERTIFICATE_PASSWORD
		opc.tcp://opcuaserver.com:48484, 10,                        Server1,                     cert.pfx              ,secret123

	# OPC TAGS TO READ FROM THE SERVER

	# OPC_TAG_PATH                        ,TYPE      ,SUBSCRIBE ,MONGO_TAG
	ns=1;s=Countries.US.Queens.Latitude   ,Double    ,Y         ,US.Queens.Latitude                
	ns=1;s=Countries.US.Queens.Longitude  ,Double    ,N         ,US.Queens.Longitude    
	# ... repeat for more servers
 