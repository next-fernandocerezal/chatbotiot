# Chatbot IoT
Trying to talk with a robotic arm using rasa nlu as nlp engine

This work uses rasa nlu version of repository https://github.com/beeva-fernandocerezal/rasa_nlu. This repository has an autodeploy version of rasa and has a manage_container script used by mqtt_connector.


The system uses four mqtt topics:

chat2thing: sends text from user to rasa nlu
thing_commands: sends rasa output to thing
thing_responses: sends thing outputs to connector
thing2chat: sends things outputs to user

Messages sent to thing_responses could be directly sent to thing2chat, but this way the thing only needs to know the name of the topics it uses (thing_commands, thing_responses), without taking care of what topic is used to talk with user.


Files:

training.json: rasa nlu training file used for debuging. The real one is provided by the arm itself.

mqtt_connector: This program is the core of the PoC, control messages flow between mqtt topics for user, rasa and thing.

mqtt_sniffer: It listen in all used mqtt topics for monitoring. Only needed for debuging.

sender_training: It sends manually the training file to rasa nlu using mqtt.

sender_msg: It sends manually a natural language message to rasa using mqtt.

