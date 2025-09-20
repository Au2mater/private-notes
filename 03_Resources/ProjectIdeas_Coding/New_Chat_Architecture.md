### Chroma Server 
A passive microservice for indexing and querying text documents 
### Agents API 
Handles bot reponses to a given conversation
Create a request session starting with a messages dict. The request can be resolved with one or multiple steps. Each intermediate step will wait for a new answer  request to be submitted. 
Returns one of the following responses, each with a status that can be sent to the conversation API. 
- a wait I am thinking response 
- a search request  this can be forwarded to the chroma API by a manager service or responded to manually 
- a call another agent request, this can also must be forwarded dby another 
- a request resolved response with a message to be added to the conversation. This message could be empty. 

### Conversation API 
Handles managing  conversations,  the conv dB and the user rights to each conv. Has no knowledge about participants outside of the conversation. 
Recieves async requests to create add update and delete messages and conversations. 
There is no LLM or chatbot action here only conversation states. 
Could euther send the messages to the non-human users agents api endpoint, or recieve a request to deliver the 
Nodes are conversations, participants, messages  and participant status. 
Has a simple non sofisticated  UI (Auto generated ) 
 
- conversation_create() -> conversation_id
- conversation_delete(conversation_id)
- invite a paraticipant to a conversation 
- join a conversation 
- leave a conversation 
- list my conversations ( 
-- conversation_add_participant(conversation_id, participant_id)
	- conversation_get(conversation id) -> {messages, participants, created) 
	- conversation_add_message(participant_if, conversation_id, message: str) 
	-
	All participants receive the entire conversation when it is updated. 
	A conversation has zero or more messages and one or more participants. 
	In a conversation each participant has at most one status. 
	A non-human participant can be a chain or an agent. 
	A paraticipant can be human or non-human. 
	The conversation rights table is a many to many  mapping of each conversation right  to users. Rights are add message, delete others messages, edit others messages and delete conversation. 
	Each participant can at any time:
	- add a message
	- update their status (writing, thinking, searching, offline, idle... )
	- change one of their messages 
	- do nothing 
	A participant can either be a user or an agent. 

### Communacations API 
￼An active service that communicates bweween chroma, agents and conversations. 
￼Forwards passive requests made by the other APIs to the proper service. 
