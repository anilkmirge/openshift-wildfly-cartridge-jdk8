# OpenShift WildFly Cartridge

This cartridge is running WildFly 8.1.0.CR1 with JDK8.  Most likely this is only temporarily needed until the OpenShift Online team provides JDK8 support on all the Nodes.

This cartridge is based on the WildFly downloadable cartridge found  [here](https://github.com/openshift-cartridges/openshift-wildfly-cartridge).  


If you find any issues, please log them in the [issues](https://github.com/ichristo/openshift-wildfly-cartridge/issues) section of the [github](https://github.com/openshift-cartridges/openshift-wildfly-cartridge) project.  

This cartridge will act very similarly to the jbossas-7 cartridge that you can create a gear with.  
You should be able to modify the code in the /src directory of the git repository, and do a git add, git commit, and git push and have it deployed as ROOT.war.  
You can also remove the pom.xml and /src directories and place a war file in the deployments directory and they should deploy like they do on JBoss AS 7  


You can build a gear using this cartridge with the following command:

	rhc app create wildfly https://cartreflect-claytondev.rhcloud.com/reflect?github=ichristo/openshift-wildfly-cartridge-jdk8
	
It will take a few minutes to build, so be patient.

### JBoss CLI

This cartridge provides an OpenShift compatible wrapper of the JBoss CLI tool on the gear PATH, located at $OPENSHIFT_WILDFLY_DIR/bin/tools/jboss-cli.sh. Use the following command to connect to the WildFly instance with the CLI tool:

        jboss-cli.sh -c --controller=$OPENSHIFT_WILDFLY_IP:$OPENSHIFT_WILDFLY_MANAGEMENT_HTTP_PORT

	corey$ rhc port-forward wildfly
	Checking available ports ... done
	Forwarding ports ...

	To connect to a service running on OpenShift, use the Local address

	Service Local               OpenShift
	------- -------------- ---- -------------------
	java    127.0.0.1:8080  =>  127.13.118.129:8080
	java    127.0.0.1:9990  =>  127.13.118.129:9990
	java    127.0.0.1:9999  =>  127.13.118.129:9999
	
In this example you would visit 127.0.0.1:9990 to view the wildfly admin panel from your local computer.
