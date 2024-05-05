# Secure Evoting System

 

 Lebanese American University
School of Arts and Sciences
Department of Computer Science and Mathematics

E-Voting System Using Blockchain and Face Recognition
CSC 437 - Networks Security - Programming Project
Presented to: Dr Khaleel Mershad

By
Mohammad Hammoud (Mohammad.hammoud14@lau.edu) 
Sarah Ibrahim (sarah.ibrahim05@lau.edu)















Introduction:
As the entire world is rapidly evolving towards incorporating technological advancements into every single aspect of our lives, e-voting has emerged as an encouraging alternative for traditional paper voting. “MS” voting platform is an innovative system aiming at securing the entire process of electronic voting. Whether for huge occasions such as national elections or even universities voting, this platform combines the power of machine learning and blockchain technology to ensure a reliable and secure experience. Although digitizing such a process offers promising prospects as speed, decreased costs, and higher convenience, it significantly faces several challenges especially in terms of reliability, authentication, and security. Thus, the blend between concise face recognition, user authentication via credentials, and a blockchain based voting process can certainly address the concerns revolving around this topic. In the same context, this platform has the potential to reshape the election experience through providing an immutable voting technique and limits the potential of impersonation. 

State of the Art:
The concept of secure e-voting has been a rising topic within the scope of researchers’ and engineers' interest for a while. Some prominent contributions to this field include papers such as “A Manipulation Prevention Model for Blockchain-Based EVoting Systems” (Tas et al., 2021), which proposes a voting system by incorporating double encryption. However, the prototype still needs further investigations due to scalability issues. Another paper in this domain is “A Conceptual Secure Blockchain-Based Electronic Voting System” (Ben Ayed, 2017), which integrates the blockchain concept into the voting process yet does not focus on the preliminary authentication stage. As for the computer vision aspect, huge progress has been made in developing face recognition models and libraries. “Face Recognition and Identification using Deep Learning Approach” (Teoh et al., 2020) sheds light on the advancements within this domain yet does not necessarily relate it to real life application scenarios. Hence, the project's primary focus is to combine the optimal features from both fields, first by ensuring a reliable authentication process through face recognition, and then by implementing a decentralized system for the voting procedure. By emerging from the solid background of the already existent contributions to this topic, “MS” voting platform aims to enhance the existing work to provide a promising future prospect.








Design and Implementation:

System Design:


The proposed system integrates face recognition for user recognition by comparing facial features from an already existing database of eligible voters photos. A successful voting process is then merged within the blockchain system to save the one-time vote.


System Components:

Face recognition module:
It is python-based using facial recognition libraries. It refers to a database of valid user faces.
Blockchain voting module: 
It uses objects and classes implemented in python as well to store and mine transactions.
Backend server:
It relies on Flask and acts as the central point of coordination of the system. It connects the authentication process and user requests with the voting operation.


System Implementation:

The frontend is simply implemented by using CSS and HTML. It combines simplicity and clarity for a smooth user experience.
The face recognition feature is implemented by mainly relying on the following libraries:
face_recognition: This library provides facial recognition capabilities, allowing you to detect faces, extract facial encodings (unique patterns representing facial features), and compare them to identify or authenticate individuals.
zlib: Used for compressing and decompressing data, likely to handle image data efficiently.
base64: Converts binary data to/from a text-based format, facilitating transmission and storage.
PIL (Python Imaging Library): Assists in manipulating and handling image files.
The blockchain code includes several files including:
block.py: This file includes the main structure of the block. The block class has attributes as index, list of transactions, timestamp, the previous hash, and the nonce. It also includes the function for computing the SHA256 hash.
blockchain.py: it initializes the list of blocks, the function for creating the genesis block, the function for adding a new block to the chain after confirming conditions, function for proof of work computation, and checking the chain validity.
certificate_authority.py: to validate specific actions and permissions within the blockchain system. It monitors the process of adding nodes to the system and maintaining their permissions.


System Operations:
Following a successful face authentication, the user shall move to the voting process. We'll be storing data in our blockchain in a format that's widely used: JSON. 
The transactions are packed into blocks. A block can contain one or many transactions. The blocks containing the transactions are generated frequently and added to the blockchain. Because there can be multiple blocks, each block should have a unique id.
We'd like to prevent any kind of tampering in the data stored inside the block, and detection is the first step to that. To detect if the data in the block is tampered, we can use cryptographic hash functions.
A hash function is a function that takes data of any size and produces data of a fixed size from it (called hash), which is generally used to identify the input. This project uses the sha256() hash function. We'll store the hash of the block in a field inside our Block object, and it'll act like a digital fingerprint (or signature) of data contained in it.
We need a mechanism to make sure that any change in the previous blocks invalidates the entire chain. The Bitcoin way to do this is creating dependency among consecutive blocks by chaining them with the hash of the block immediately previous to them. By chaining here, we mean to include the hash of the previous block in the current block in a new field called previous_hash.
The very first block is called the genesis block and can be generated either manually or by some unique logic. Let's add the previous_hash field to the Block class and implement the initial structure of our Blockchain class.
If we change the previous block, we can re-compute the hashes of all the following blocks quite easily and create a different valid blockchain. To prevent this, we will now exploit the asymmetry in efforts of hash functions that we discussed previously to make the task of calculating the hash difficult and random. Here's how we do this. Instead of accepting any hash for the block, we add some constraint to it. Let's add a constraint that our hash should start with "n leading zeroes" where n can be any positive integer.
To add a block to the chain, we'll first have to verify that the data is untampered i.e., the Proof of Work provided is correct, and the order of transactions is preserved i.e., the previous_hash field of the block to be added points to the hash of the latest block in our chain.
The transactions will be initially stored as a pool of unconfirmed transactions. The process of putting the unconfirmed transactions in a block and computing Proof of Work is known as the mining of blocks. Once the nonce satisfying our constraints is figured out, we can say that a block has been mined, and it can be put into the chain.



4. Conclusion:

The proposed system supports strong user verification through the face recognition followed by the following features offered by the blockchain implementation:
Authentication: Only people already registered to vote can cast a vote. Our system will not support a registration process. Registration usually requires verification of certain information and documents to comply with current laws, which could not be done online in a secure manner. Therefore, the system should be able to verify voters’ identities against a previously verified database, and then let them vote only once.
Anonymity: The e-Voting system should not allow any links between voters’ identities and ballots. The voter has to remain anonymous during and after the election.
Accuracy: Votes must be accurate; every vote should be counted, and can’t be changed, duplicated or removed.
Verifiability: The system should be verifiable to make sure all votes are counted correctly. Beside the main requirement, our solution supports mobility, flexibility, and efficiency.
Overall, the system aims for a secure and anonymous voting procedure that shall save time and resources. As for future limitations, the system process shall be automated to avoid manual mining, but rather set an automatic time interval to mimic real-life blockchain systems. It shall also be tested on multiple networks and not locally on a single device as we did for convenience purposes.
