# Performance benchmark commands

### General

### JMH

Yourkit
    
    java -agentpath:/Applications/YourKit\ 2013.app/bin/mac/libyjpagent.jnilib -jar target/benchmarks.jar -wi 10 -i 5 -f 1 -tu ns -bm avgt "Class.*Stream.*filterAndMapSeq.*" -p size="1000" -prof stack