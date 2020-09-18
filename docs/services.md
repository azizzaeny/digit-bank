
Lets sit back prepare the  blank canvas, and  start asking questions    

WHAT DO WE NEED TODO.  

**Service Design**   

 At system level each component configured as "infrastructure as code" meaning configuration of ports database services routes, kafka consumer/producers declared as data, and push to the last any technical implementations details.   


 Functional programming at hearth and hexagonal architecture. separating the concerns of core logic or business logic with controller side-effects, making single responsibility functions, taking care of input the processing line and the output mechanism.  


 Using kafka as core channel messaging between services, we project the domain business with mongodb, and serve the api gateways in nodejs http rest with only take one routes and only post post methods. every request and response is logged in i/o topics with retention policy of 1 days.  
 
 As for authentication and authorizations, we use json webtoken, no-cookies, no-session in the server. the auth processor will have their own computing power which is mean different nodeservices.   


 The server and backend api it self is dummy, they only map input and take output. no logic in each of them. every request will be blocked and attached request-id and client-id send them into topics and watch them back as response. the long request or heavy request such us write or delete, will be called asyncrhonously and the user will get back the result as pending queue.  


 Each service node will wrapped in docker container and composed as single orchestrations network. for example it bundle up zookeeper, kafka and mongodb as needed. make node.js runner in container as stack of processing power.  


 Security and scale. we start move slowly and use plaintext alot which is mean we configure it properly later on when the requirements call needed.   


 Every request to the api gateways should include authorizations headers and its bearer token value.to generate the token every user should send request to the api gateway with basic authorizations and the server will unwrap the basic auth into desired authentication type.  even if it use ssl in the ends and can be easy decode at least we will not send it as plain passwords   


 Hexagonal architecture or onion design. Hexagonal consist of several parts. 1.ports, 2.adapter 3.controller, 4. core logic. ports implement external communications component standard protocol and library use. adapter will manage schema endpoints translate input and manage the output. controller will fetch data from db and run business logic, controller will wire business logic and side-effect things. core logic will be pure-functions, a logic only contain specs and model the real world business.  


We also implements event driven designs, stored all events and meta data permanently in kafka topics. it will be usefull for audit trails.   








 
 
 
 
 
 
 
