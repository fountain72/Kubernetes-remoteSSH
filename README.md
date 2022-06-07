# Kubernetes-remoteSSH
send remote SSH command to the pod(s) with wildcard or specific pod names


# rmtKmd

Remote Commands to send commands across all PODs/Containers within the same Namespace.

version 2.0    02/26/2022

Type -h or --help for a full list of available options.

Cheat sheet:

1) To run on all Pods and containers, just give namespace options with -n NAMESPACES, no need
   to give option with -p or -c
   example:

   rmtKmd -n NAMESPACE -q "date;time"

2) for "-p PODS", you can give multiple POD name seperated by comma, or the common part of their name,
   if given with "-" at the beginning or the end of option, please run as "-p=-xdms" (example)

   example:

   rmtKmd -n NAMESPACE -p podA,podB -q "date;time"
   rmtKmd -n NAMESPACE -p podA-1,podB-0 -q "date;time"
   rmtKmd -n NAMESPACE -p=-rcs -q "date;time"

3) To run multiple lines command option please refer the example below

   rmtKmd -n NAMESPACES -p podA-0 -q "cli << EOF
   > show table;
   > EOF"
