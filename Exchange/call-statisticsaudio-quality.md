---
title: Call Statistics > Audio Quality
ms.prod: EXCHANGE
ms.assetid: bb92b70e-ba23-4b62-a65d-bffd7161f3c5
---


# Call Statistics > Audio Quality

If your organization is experiencing problems with the audio quality of Unified Messaging (UM) calls and voice mail messages, use the **Call statistics** report to help you understand what's causing the problems.
  
    
    


> [!NOTE]
> The audio quality of a call can be affected by factors that aren't covered in the reports. For example, if a Mailbox server is experiencing a heavy memory load or CPU load, users may report poor call quality, even though the reports show excellent audio quality. 
  
    
    


To get more details about the audio quality for a row in the report, select the row and click **Audio Quality Details**.
  
    
    


- **Date and Time:** The UTC date and time that the call statistics were captured.
    
  
- **UM dial plan:** The dial plan for the calls included in the statistics.
    
  
- **UM IP gateway:** The gateway that took the calls included in the statistics.
    
  
- **NMOS:** The Network Mean Opinion Score (NMOS) score for the call. The NMOS score indicates how good the audio quality was on the call as a number on a scale from 1 to 5, with 5 being excellent.
    
    > [!NOTE]
      > The maximum NMOS possible for a call is dependent on the audio codec being used, and NMOS may not be available for very short calls that are less than 10 seconds long. 
- **NMOS degradation:** The amount of audio degradation of the NMOS score from the top value possible for the audio codec being used. For example, if the NMOS degradation value for a call was 1.2 and the NMOS reported for the call was 3.3, the maximum NMOS score for that particular call would be 4.5 (1.2 + 3.3).
    
  
- **Jitter:** The average variation in the arrival of data packets for the call.
    
  
- **Packet loss:** The average percentage of data packet loss for the selected call. Packet loss is an indication of the reliability of the connection.
    
  
- **Round trip:** The average round-trip score, in milliseconds, for audio on the selected call. The round-trip score measures latency on the connection.
    
  
- **Burst loss duration:** The average duration of packet loss during bursts of losses for the selected call.
    
  
- **Number of samples:** The number of calls that were sampled to calculate the averages.
    
  

