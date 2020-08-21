# Simple run JFR
    
    -XX:+UnlockDiagnosticVMOptions 
    -XX:+UnlockCommercialFeatures 
    -XX:+FlightRecorder 
    -XX:+DebugNonSafepoints 
    -XX:StartFlightRecording=name=Profiling,duration=20s,delay=10s,filename=C:\Temp\myrecording.jfr,settings=profile
  
