Steps to publish a full set of MicroProfile TCK results

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