# Datasets
Sample Datasets for Machine Learning and deeplearning
https://www.tutorialspoint.com/python_pandas/python_pandas_groupby.htm

ubuntu@ec2-18-222-110-54.us-east-2.compute.amazonaws.com
8888
172.31.14.159:3389


https://drive.google.com/file/d/1TaClmJz40Pi4ZAR4vZYI7eVe2ojpXK__/view
# -*- coding: utf-8 -*-

https://github.com/cpopp/MicroTelnetServer/blob/master/utelnet/utelnetserver.py

https://pythonprogramminglanguage.com/telnet/
**************************************************************
# telnet program example
import socket, select, string, sys

#main function
if __name__ == "__main__":
	
	if(len(sys.argv) < 3) :
		print ('Usage : python telnet.py hostname port')
		sys.exit()
	
	host = sys.argv[1]
	port = int(sys.argv[2])
	
	s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
	s.settimeout(2)
	
	# connect to remote host
	try :
		s.connect((host, port))
	except :
		print('Unable to connect')
		sys.exit()
	
	print('Connected to remote host')
	
	while 1:
		socket_list = [sys.stdin, s]
		
		# Get the list sockets which are readable
		read_sockets, write_sockets, error_sockets = select.select(socket_list , [], [])
		
		for sock in read_sockets:
			#incoming message from remote server
			if sock == s:
				data = sock.recv(4096)
				if not data :
					print ('Connection closed')
					sys.exit()
				else :
					#print data
					sys.stdout.write(data)
			
			#user entered a message
			else :
				msg = sys.stdin.readline()
				s.send(msg)
