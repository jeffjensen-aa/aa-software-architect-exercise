# Exercise 3    

![Exercise3.architecture.jpg](ArchitectureDiagram/Exercise3.architecture.jpg?raw=true)

<br>

![Exercise3.Sequence.jpg](SequenceDiagram\Exercise3.Sequence.jpg?raw=true)


## Diagram Details
The application is triggered by a flight event from the event hub. The Canceled Flight Event Handler could either be a Spring Boot Function app or a Runway / Kubernetes Spring Boot application. Depending on time / money constraints. <br>


After an event has triggered the application, a call to the Flight Status Service would retrieve the cancellation reason. If the cancellation was because of Crew or Maintenance, the application would continue, otherwise it would stop processing. Once it has been determined the flight was canceled due to Crew or Maintenance issues, An availability check would be performed to see if there are any more available flights to accommodate passengers that were on the canceled flight. If there are no other flight options available, an eligible passenger provider would provide the list of passengers that were eligible to receive voucher notifications. The notifications would then be sent using the notification service.