# Supported tags and respective `Dockerfile` links

- [`3.0.3.778-1`, `latest`, (*Dockerfile*)](https://github.com/developertown/sonar-scanner/blob/master/3.0.3.778/Dockerfile)

# Containerized Sonar Scanner

This image packages up the Sonar Scanner CLI utility to make it easier to run on any machine

## How to use this image

Simply volume mount the root of your project directory (which should contain a `sonar-project.properties` file) like this.  You may optionally mount a volume to /root/.sonar to speed up subsequent builds (avoiding cost of downloading plugin .jar's each time)

## Example

    docker run --rm -it \
      -v /path/to/my/project/on/host:/project \
      -v sonar-cache:/root/.sonar \
      sonar-scanner
