# primes
import zmq

class Replica: 
	

	
	def __init__(self, isLeader, agentID): 
		numReplicas = 3
		self.port = [5885, 5886, 5887] # port numbers of each of the replicas
		self.ID = agentID # 
		context = zmq.Context()
		socket = context.socket(zmq.PUSH)
		self.isLeader = isLeader # determines if a replica is the leader, either 0 or 1
		self.agentVal = 0 # the value that the replica holds 
		self.proposalNum = 0 # the number that keeps track of the leaders

		#self.start(self, port, agentVal) I dont know if it need these
		#self.start(self)


	def start(self):
		status()

		



	def status(self):
		context = zmq.Context()
		if self.isLeader == 1:
			self.prepare(self, agentVal, proposalNum)
			numOfResponses = 0
			while numOfResponses < ((numReplicas/2) + 1):
				# (fill in with number of responses)

				numOfResponses++

	
		


	# prepare request made by the leader and the acceptor's response to this prepare request
	def prepare(self):
		context = zmq.Context()
		if self.isLeader == 1:
			# bind to the socket
			leader_socket = context.socket(zmq.PUSH)
			leader_socket.bind("tcp://127.0.0.1:5885")
			# prepare request asks for a promise and the proposal 
			# with the highest number less than the current leader's proposal num
			prepareRequest = {'promise' : False, 'proposalNum' : 0, 'agentVal' : 0} 
			leader_socket.send_json(prepareRequest)
		else:
			acceptor_receiver = context.socket(zmq.PULL)
			acceptor_receiver.connect("tcp://127.0.0.1:5885")
			prepareResponse = acceptor_receiver.recv_json()
			# responding to prepare request with the requested elements
			
			if # this if statement is meant to check if the proposal number of 
			# the current leader is less than the proposal number of any other 
			# leader the acceptor has accepted so far
				prepareResponse['promise'] = True # if the proposal number of the current leader is greater than the proposal number of any other leader the acceptor has accepted so far, then make the promise "True"




	def accept(self):
		context = zmq.Context()
		if self.isLeader == 1:

		else:
			







