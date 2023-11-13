Ultimate list of useful commands and flags for java developers

# Monitoring

### Native memory tracking

Start the JVM with summary or detail tracking using the command line option

    -XX:NativeMemoryTracking=summary

or

    -XX:NativeMemoryTracking=detail

###  Enable heap dump on OOM

    -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/opt/tmp/heapdump.bin

# Performance

### JMH

Set number of iterations

    java -jar target/benchmarks.jar -wi 20 -i 10 -f 1 -tu ns -bm avgt -rf text -rff results/benchmarks-8.txt -o log.txt

Analyse

    java -XX:+UnlockDiagnosticVMOptions -XX:+TraceClassLoading -XX:+PrintCompilation -XX:+LogCompilation -XX:+PrintAssembly -jar target/benchmarks.jar -wi 1 -i 5 -f 1 -tu us -bm avgt -prof comp ".*Inline.*calculateInline.*"

Yourkit

    java -agentpath:/Applications/YourKit\ 2013.app/bin/mac/libyjpagent.jnilib -jar target/benchmarks.jar -wi 10 -i 5 -f 1 -tu ns -bm avgt "Class.*Stream.*filterAndMapSeq.*" -p size="1000" -prof stack

### Async profile commands

    ./profiler.sh -t -d 10 -o collapsed -f /tmp/tts.collased --begin SafepointSynchronize::begin --end RuntimeService::record_safepoint_synchronized SafepointApplication

# Utilities

### Concurrency

Randomizes instruction scheduling. It allows finding concurrency bugs that would be otherwise hidden on a given architecture.

`-XX:+StressLCM / -XX:+StressGCM`