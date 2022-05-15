# Building

### Build slowdebug-mode images for experiments

    git clone --depth 1 https://github.com/openjdk/jdk11u-dev.git
    cd jdk11u-dev
    bash configure --with-debug-level=slowdebug
    make images

Run the code:

    ./build/linux-x86_64-normal-server-slowdebug/jdk/bin/java -Xmx700M -XX:+AlwaysPreTouch -XX:+SafepointTimeout -XX:SafepointTimeoutDelay=100 -XX:+UnlockDiagnosticVMOptions -XX:+AbortVMOnSafepointTimeout Temp

It now has way more details:

    Current thread (0x00007f12b401e800):  JavaThread "main" [_thread_in_vm, id=3325, stack(0x00007f12bd06b000,0x00007f12bd16c000)]

    Stack: [0x00007f12bd06b000,0x00007f12bd16c000],  sp=0x00007f12bd168148,  free space=1012k
    Native frames: (J=compiled Java code, A=aot compiled Java code, j=interpreted, Vv=VM code, C=native code)
    C  [libc.so.6+0x15baa1]  __memmove_ssse3_back+0x1b11
    V  [libjvm.so+0x30bd40]  Copy::conjoint_jbytes(void const*, void*, unsigned long)+0x2b
    V  [libjvm.so+0x30b6a8]  void AccessInternal::arraycopy_conjoint<signed char>(signed char*, signed char*, unsigned long)+0x2b
    V  [libjvm.so+0xc03380]  EnableIf<(((!HasDecorator<64ul, 4ul>::value)&&(!(HasDecorator<64ul, 33554432ul>::value&&RawAccessBarrierArrayCopy::IsHeapWordSized<signed char>::value)))&&(!HasDecorator<64ul, 67108864ul>::value))&&(!HasDecorator<64ul, 134217728ul>::value), void>::type RawAccessBarrierArrayCopy::arraycopy<64ul, signed char>(arrayOopDesc*, unsigned long, signed char*, arrayOopDesc*, unsigned long, signed char*, unsigned long)+0x6d
    V  [libjvm.so+0xc03218]  bool RawAccessBarrier<64ul>::arraycopy<signed char>(arrayOopDesc*, unsigned long, signed char*, arrayOopDesc*, unsigned long, signed char*, unsigned long)+0x48
    V  [libjvm.so+0xc03119]  EnableIf<HasDecorator<2642000ul, 4096ul>::value&&AccessInternal::PreRuntimeDispatch::CanHardwireRaw<2642000ul>::value, bool>::type AccessInternal::PreRuntimeDispatch::arraycopy<2642000ul, signed char>(arrayOopDesc*, unsigned long, signed char*, arrayOopDesc*, unsigned long, signed char*, unsigned long)+0x48
    V  [libjvm.so+0xc02fd2]  EnableIf<!HasDecorator<2637904ul, 4096ul>::value, bool>::type AccessInternal::PreRuntimeDispatch::arraycopy<2637904ul, signed char>(arrayOopDesc*, unsigned long, signed char*, arrayOopDesc*, unsigned long, signed char*, unsigned long)+0x59
    V  [libjvm.so+0xc02e96]  bool AccessInternal::arraycopy_reduce_types<2637904ul, signed char>(arrayOopDesc*, unsigned long, signed char*, arrayOopDesc*, unsigned long, signed char*, unsigned long)+0x48
    V  [libjvm.so+0xc02cf6]  bool AccessInternal::arraycopy<2621440ul, signed char>(arrayOopDesc*, unsigned long, signed char const*, arrayOopDesc*, unsigned long, signed char*, unsigned long)+0x50
    V  [libjvm.so+0xc02a56]  void Access<2621440ul>::arraycopy<signed char>(arrayOopDesc*, unsigned long, signed char const*, arrayOopDesc*, unsigned long, signed char*, unsigned long)+0x4d
    V  [libjvm.so+0xcc85aa]  void ArrayAccess<0ul>::arraycopy_to_native<signed char>(arrayOopDesc*, unsigned long, signed char*, unsigned long)+0x47
    V  [libjvm.so+0xcbe07e]  jni_GetByteArrayRegion+0x2f4
    C  [libjava.so+0x1e858]  writeBytes+0x15d
    C  [libjava.so+0x10d86]  Java_java_io_FileOutputStream_writeBytes+0x5b
    j  java.io.FileOutputStream.writeBytes([BIIZ)V+0 java.base
    j  java.io.FileOutputStream.write([BII)V+16 java.base
    j  java.io.BufferedOutputStream.write([BII)V+20 java.base
    j  java.io.FilterOutputStream.write([B)V+5 java.base
    j  Temp.main([Ljava/lang/String;)V+58
    v  ~StubRoutines::call_stub
    V  [libjvm.so+0xbebc5d]  JavaCalls::call_helper(JavaValue*, methodHandle const&, JavaCallArguments*, Thread*)+0x647
    V  [libjvm.so+0x10a88dc]  os::os_exception_wrapper(void (*)(JavaValue*, methodHandle const&, JavaCallArguments*, Thread*), JavaValue*, methodHandle const&, JavaCallArguments*, Thread*)+0x32
    V  [libjvm.so+0xbeb614]  JavaCalls::call(JavaValue*, methodHandle const&, JavaCallArguments*, Thread*)+0xa8
    V  [libjvm.so+0xc96122]  jni_invoke_static(JNIEnv_*, JavaValue*, _jobject*, JNICallType, _jmethodID*, JNI_ArgumentPusher*, Thread*)+0x1f0
    V  [libjvm.so+0xcad204]  jni_CallStaticVoidMethod+0x36a
    C  [libjli.so+0x5062]  JavaMain+0xcf7

