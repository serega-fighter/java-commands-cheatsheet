# Simple run JFR args
    
    -XX:+UnlockDiagnosticVMOptions 
    -XX:+UnlockCommercialFeatures 
    -XX:+FlightRecorder 
    -XX:+DebugNonSafepoints 
    -XX:StartFlightRecording=name=Profiling,duration=20s,delay=10s,filename=C:\Temp\myrecording.jfr,settings=profile,stackdepth=512

# Custom JFR events

https://inside.java/2022/04/25/sip48/

# Analyze JFR

https://github.com/moditect/jfr-analytics

# JMC Agent

https://developers.redhat.com/blog/2020/10/29/collect-jdk-flight-recorder-events-at-runtime-with-jmc-agent#