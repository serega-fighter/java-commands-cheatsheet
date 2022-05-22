# Memory

# Heap dump

    -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/opt/tmp/heapdump.bin

# Native memory tracking

Start the JVM with summary or detail tracking using the command line option

    -XX:NativeMemoryTracking=summary

or

    -XX:NativeMemoryTracking=detail