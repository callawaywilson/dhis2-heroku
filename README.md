# DHIS2 - Heroku Deployment Container

This repository contains the configuration and Jetty runner to run DHIS2 on Heroku.  BYODB (Bring your own Database).  It should be built using the default Java buildpack.

More detailed instructions on configuring and running DHIS2 can be found in the DHIS2 documentation:

[https://docs.dhis2.org/2.28/en/implementer/html/install_server_setup.html](https://docs.dhis2.org/2.28/en/implementer/html/install_server_setup.html)


### Deployment Instructions

The container works by piping environmnent variables to the dhis.conf file in the root of the project.  These are the required variables:

    * `DHIS2_HOME` - Must be '.', location of dhis.conf
    * `DHIS2_DATABASE_URL` - JDBC URL of Postgres DB for DHIS2
    * `DHIS2_DATABASE_USERNAME` - Username of Postgres DB User for DHIS2
    * `DHIS2_DATABASE_PASSWORD` - Passowrd of Postgres DB User for DHIS2
    * `DHIS2_ENCRYPTION_PASSWORD` - Data encryption password for DHIS2

Optional variables:

    * `JAVA_OPTS` - JVM Options, it's a good idea to limit memory available on Heroku Dynos

The Procfile will try to deploy `dhis.war` in the root of the directory, so download DHIS2 from

[https://www.dhis2.org/downloads](https://www.dhis2.org/downloads)

and place the war in the root directory.  Commit the war and push to your Heroku project.