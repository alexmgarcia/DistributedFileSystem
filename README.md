# DistributedFileSystem

This is an academic assignment for the Distributed Systems course which is a Distributed File System

It is a community of servers on which the client can operate as it is just one server (using Java RMI or WebServices and SSL). It supports the commands servers, ls dir, mkdir dir, rmdir dir, cp path1 path2, rm path, getattr path

It also has a proxy to Dropbox, Google Drive and Flickr allowing to sync a directory with this services

## How to run

### Server

 	java DirServerWS [-p Port] [-bp BasePath] community [URL] serverIPAddress
 	
 	java DirServerRMI [-bp BasePath] community [URL] serverIPAddress

If no parameter is specified in -p the default port is 8080

If no parameter is specified in -bp the default basepath is "."

- Start first WS server:

		java tp2.DirServerWS -p Port -bp basePath communityname ip

- Start first RMI server: 

		java tp2.DirServerRMI -bp basePath communityname ip
		
NOTE: If the tp2 package is not specified (tp2.) an error will be returned (main method notfound)

NOTE2: It is necessary to have the SSL certificates in bin directory

- Start more WS server: 

		java tp2.DirServerWS -p Port -bp basePath communityname urlofanotherserver ip

- Start more RMI server:

		java tp2.DirServerRMI -bp basePath communityname urlofanotherserver ip
				
- Start Google DriveRMI server: 

		java -cp .;commons-codec-1.7.jar;json-simple-1.1.1.jar;scribe-1.3.2.jar tp2.DirServerGoogleDriveRMI communityname ip

- Start DropBoxRMI server: 

		java -cp .;commons-codec-1.7.jar;json-simple-1.1.1.jar;scribe-1.3.2.jar tp2.DirServerDropBoxRMI communityname ip
	
- Start FlickrRMI server: 

		java -cp .;commons-codec-1.7.jar;json-simple-1.1.1.jar;scribe-1.3.2.jar tp2.DirServerFlickrRMI communityname ip

### Client

- Start the client using multicast server search: 

		java -cp .;json-simple-1.1.1.jar tp2.FileClient
		
- Start the client using an URL of a server: 

		java -cp .;json-simple-1.1.1.jar tp2.FileClient serverurl
	
NOTE: To successfully end a client it is necessary to use the command exit to logout from servers
