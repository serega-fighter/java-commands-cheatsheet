# Running jstatd
Create a file named jstatd.all.policy

    grant codebase "file:${java.home}/../lib/tools.jar" {
        permission java.security.AllPermission;
    };

Run jstatd via command

    jstatd -p 1099 -J-Djava.security.policy=~/jstatd.all.policy

# Adding JMX connection (allows remote CPU/method sampling)

    -Dcom.sun.management.jmxremote.port=3333 -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false
