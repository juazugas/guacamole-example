# Guacamole Simple sample server

Simple tunnel example with ~~hard-coded~~ configuration parameters.

Based on example for expose guacamole through guacamole-client.

Look original project [guacamole/guacamole-client/doc/guacamole-example](https://github.com/apache/guacamole-client/tree/master/doc/guacamole-example)

### Development 

Clone this repository and compile the sources.

```
mvn clean compile package
```

This produces the `-thorntail.jar` file that runs an embedded undertow. 

To launch the example you can run the thorntail plugin

```
mvn thorntail:run 
```

Or launch the java application directly 

```
java -jar target/guacamole-example-1.1.0-thorntail.jar
```


NOTE:
If you want the latest sources ...
Clone the guacamole-client github project, and install the SNAPSHOT version of the guacamole-common and guacamole-commonjs in your local repository.

### Config parameters

This project is using the microprofile config specification to parameterize the connection values, 
the properties that can be used are : 

- `"guacamole.connection.guacd.hostname"` : Hostname running the guacamole server, default "localhost".

- `"guacamole.connection.guacd.port"` : Port exposing the guacamole server, default 4822.

- `"guacamole.connection.vnc.hostname"` : Hostname running the vnc server that the guacamole server has to connect to, default "localhost".

- `"guacamole.connection.vnc.port"` : Port exposing the vnc server, default "5901". 

This properties can be specified as System properties or any form supported by the thorntail microprofile specification.

More information can be found in [microprofile-config](https://github.com/eclipse/microprofile-config), the default ConfigSource configuration,
e.g. : 

`java -jar target/guacamole-example-thorntail.jar -Dguacamole.connection.vnc.port=5902 ...`

### Logging 

The logging can be activated using the System property for thorntail loggin (more information can be in the Thorntail documentation):

`java -jar target/guacamole-example-thorntail.jar -Dthorntail.logging=FINE  ...`

### Requisites 

You need a vnc server running, and the guacamole server with network connection to the vnc server.

Command example of running a guacamole server using containers could be: 

`podman run --net=host --name some-guacd -d -p 4822:4822 guacamole/guacd`

### Resources 

- Guacamole-client Github Sources
https://github.com/apache/guacamole-client/

- Guacamole FAQ.
https://guacamole.apache.org/faq/#iframes

- Guacamole with docker.
https://guacamole.apache.org/doc/gug/guacamole-docker.html

- Thorntail Servlet .war Example
https://github.com/thorntail/thorntail-examples/tree/master/servlet/servlet

- Microprofile Config github 
https://github.com/eclipse/microprofile-config

- Thorntail Documentation (version 2.5.0.Final)
https://docs.thorntail.io/2.5.0.Final/#_web
