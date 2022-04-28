# Simple run JFR args
    
    -XX:+UnlockDiagnosticVMOptions 
    -XX:+UnlockCommercialFeatures 
    -XX:+FlightRecorder 
    -XX:+DebugNonSafepoints 
    -XX:StartFlightRecording=name=Profiling,duration=20s,delay=10s,filename=C:\Temp\myrecording.jfr,settings=profile,stackdepth=512

# Analyze JFR

https://github.com/moditect/jfr-analytics
