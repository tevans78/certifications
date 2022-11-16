## Steps to locally create a page of beta MicroProfile TCK results

It is recommended to run the TCK using Semeru Certified Editions. 

### For Java 11 results:
1. Extract the beta runtime somewhere.

2. Create a new server in the `wlp/usr/servers` directory. Place a copy of the files from the test bucket’s `publish/servers` folder, i.e. in the `server.xml` and any other server config. 

3. In the TCK runner test, comment out anything to do with starting and stopping the server.
    Do not change the server name in the TCK runner test - the FAT framework is still going to set up a server as usual but we do not want to start it as the tests will run on the separate server from the previous steps.

4. In the `arquillian.xml`, change the values for `wlpHome`, `serverName` and `httpPort` to match the install directory from step 1 and the server name from step 2.

5. Start the server from the command line and make sure that the JAVA_HOME is correctly set before doing this.

6. Run the TCK project from a separate command line.
    Make sure JAVA_HOME is set to the same value before doing this
    If JAVA_HOME was not set, you need to run 
    ```
    ./gradlew --stop
    ```
    for the gradle daemon to pick up the change to JAVA_HOME.

It is important to check the server logs verify that the TCK actually ran on your server. Check the `emailable-report.html` to check that your passing tests do not also report exceptions. 

### For Java 17 results
Change your Java version to 17 before running the server before running steps 1-5. 
Change the Java version back to 11 in the terminal for step 6 and run the TCK. The `messages.log` file in the server directory should show that the tests ran in Java 17. Be aware that the generated results will show the Java version used for the gradle command.

## Steps to publish a full set of MicroProfile TCK results

1. Create a folder structure using this pattern `/microprofile/<MP version>/<spec>/<version>`
2. Add results files for the Java versions being certified `<Liberty-version>-<Spec>-<Spec-version>-<Java-version>-TCKResults.adoc`
    e.g.
    ```
        microprofile/6.0/
            config/3.0.2/
                22.0.0.13-beta-Config-3.0.2-Java11-TCKResults.adoc
                22.0.0.13-beta-Config-3.0.2-Java17-TCKResults.adoc
            faulttolerance/4.0.2/
                22.0.0.13-beta-Fault-Tolerance-4.0.2-Java11-TCKResults.adoc
                22.0.0.13-beta-Fault-Tolerance-4.0.2-Java17-TCKResults.adoc
            health/4.0.1/
                22.0.0.13-beta-Health-4.0.1-Java11-TCKResults.adoc
                22.0.0.13-beta-Health-4.0.1-Java17-TCKResults.adoc
            jwt/2.1/
                22.0.0.13-beta-JWT-Auth-2.1-Java11-TCKResults.adoc
                22.0.0.13-beta-JWT-Auth-2.1-Java17-TCKResults.adoc
            metrics/5.0.0/
                22.0.0.13-beta-Metrics-5.0.0-Java11-TCKResults.adoc
                22.0.0.13-beta-Metrics-5.0.0-Java17-TCKResults.adoc
            openapi/3.1/
                22.0.0.13-beta-Open-API-3.1-Java11-TCKResults.adoc
                22.0.0.13-beta-Open-API-3.1-Java17-TCKResults.adoc
            restclient/3.0.1/
                22.0.0.13-beta-Rest-Client-3.0.1-Java11-TCKResults.adoc
                22.0.0.13-beta-Rest-Client-3.0.1-Java17-TCKResults.adoc
            telemetry/1.0/
                22.0.0.13-beta-Telemetry-1.0-Java11-TCKResults.adoc
                22.0.0.13-beta-Telemetry-1.0-Java17-TCKResults.adoc
    ```

3. Draft versions of these results files can be found in the "TCK Results" downloads for each build. Note that these are only draft/templates and will need to be updated manually.
    - If the results are being taken from a build which has been SOE'd then there will be results for a large number of platforms. You should choose a consistent set of results from just one platform, preferably running with a Semeru JVM. e.g. `RHEL8_X86_IBM_SEMERUJDK11_CERTIFIED_64_EBC`
    - Make sure that the Liberty version is correct if using the beta rather than GA version
    - Ensure that all links within the results are correct.
    - In some cases you may have to make an educated guess about what the URL will be when released.