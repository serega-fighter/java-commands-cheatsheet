# Basic

### Profile for long safepoint pauses

    ./profiler.sh -t -d 10 -o collapsed -f /tmp/tts.collased --begin SafepointSynchronize::begin --end RuntimeService::record_safepoint_synchronized SafepointApplication