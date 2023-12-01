# Async profiler

### Profile for long safepoint pauses

    ./profiler.sh -t -d 10 -o collapsed -f /tmp/tts.collased --begin SafepointSynchronize::begin --end RuntimeService::record_safepoint_synchronized SafepointApplication

# Profile for allocation

Sometimes it's useful to disable TLAB if one wants to profile allocations with JFR

    -XX:-UseTLAB

# JFR

    -XX:+UnlockDiagnosticVMOptions 
    -XX:+UnlockCommercialFeatures 
    -XX:+FlightRecorder 
    -XX:+DebugNonSafepoints 
    -XX:StartFlightRecording=name=Profiling,duration=20s,delay=10s,filename=C:\Temp\myrecording.jfr,settings=profile,stackdepth=512

# Generate profile

To help make event configuration easier, a new configure command was added to the jfr tool:

    jfr configure

Another example

    jfr configure exceptions=all --output exceptions.jfc

Then use custom profile

    java -XX:StartFlightRecording:settings=custom.jfc -jar app.jar

# Custom JFR events

### Events

https://inside.java/2022/04/25/sip48/

### Per events settings

    @Name("com.company.HttpGetRequest")
    @Label("HTTP GET Request")
    @Category("HTTP")
    @Enabled(false)
    @StackTrace(false)
    @Threshold("0 ms")
    public class HttpGetRequest extends jdk.jfr.Event {
        @Label("Request URI")
        String uri;
    }
    
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) {
        HttpGetRequest request = new HttpGetRequest();
        request.begin();
        request.uri = req.getRequestURI();
        ...
        request.commit();
    }

To add the event to a configuration file, specify the event name, followed by “#” and a key-value pair:

    jfr configure +com.company.HttpGetRequest#enabled=true --output http.jfc

# Analyze JFR

https://github.com/moditect/jfr-analytics

# JMC Agent

https://developers.redhat.com/blog/2020/10/29/collect-jdk-flight-recorder-events-at-runtime-with-jmc-agent#