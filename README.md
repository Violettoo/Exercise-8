# Exercise-8: Time-Series Architecture

Question 1: The Definition of Metadata 

  i) Why must metadata be a static identifier? Metadata must be static because MongoDB uses it as a hard routing key to bucket incoming sequential streams. Under the Bucket Pattern, the engine collapses a sequence of sequential events from the exact same source into a single compressed block on your disk layout.
  
  ii) What happens if it changes every second? If you map a rapidly changing metric (like temperature) to the metaField, every fractional change in the reading forces the database to open a completely new bucket allocation on the hard drive. This breaks data compression completely, wastes memory, and slows processing speeds.  
  
  Question 2: Middleware vs. Edge Timestamping   
  
    i) Why is server-side timestamping safer? Cheap edge hardware, like a basic $5 ESP32 microcontroller, does not contain an internal battery-backed Real-Time Clock (RTC) hardware module. If the microcontroller resets or experiences a power brownout, its system timer resets to zero.  
    
    ii) Generating the chronological tracker sequence (new Date()) inside the Node-RED middleware layer guarantees that your time-series archive remains bound to a precise, highly accurate, centralized system universal clock
