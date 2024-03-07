
# State diagram example

````mermaid
stateDiagram-v2

s1: Service is starting up
s2: Service is waiting for tasks
s3: Running a task
s4: Service is crashed
s5: Service is shut down successuflly

[*] --> s1
s1 --> s2 
s2 --> s3 
s3 --> s2 : Task completes successfully
s3 --> s4 : Something goes wrong
s2 --> s5
s4 --> [*]
s5 --> [*]

````