# Performance benchmark commands

### General

### JMH

Set number of iterations

    java -jar target/benchmarks.jar -wi 20 -i 10 -f 1 -tu ns -bm avgt -rf text -rff results/benchmarks-8.txt -o log.txt

Analyse

    java -XX:+UnlockDiagnosticVMOptions -XX:+TraceClassLoading -XX:+PrintCompilation -XX:+LogCompilation -XX:+PrintAssembly -jar target/benchmarks.jar -wi 1 -i 5 -f 1 -tu us -bm avgt -prof comp ".*Inline.*calculateInline.*"

Yourkit

    java -agentpath:/Applications/YourKit\ 2013.app/bin/mac/libyjpagent.jnilib -jar target/benchmarks.jar -wi 10 -i 5 -f 1 -tu ns -bm avgt "Class.*Stream.*filterAndMapSeq.*" -p size="1000" -prof stack

