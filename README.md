# PHP Development Docker Image with Xdebug Support

This repository contains a customized Docker image for PHP development with Xdebug support. It provides an easy and consistent environment for PHP developers to write, test, and debug their applications.

## Features

- **PHP**: The image is based on the latest stable version of PHP, ensuring compatibility with modern PHP applications.
- **Xdebug**: Xdebug is preconfigured and enabled in the image, allowing seamless debugging of PHP code.
- **Composer**: Composer, the dependency manager for PHP, is preinstalled in the image, making it convenient to manage project dependencies.
- **Extensions**: The image includes commonly used PHP extensions, such as PDO, mysqli, gd, and mbstring, providing a rich development environment.
- **Custom Configuration**: The PHP configuration has been customized to suit development needs, including error reporting settings, time zone configuration, and memory limits.

## Prerequisites

- [Docker](https://www.docker.com/) must be installed on your machine.

## Usage

1. Clone this repository to your local machine:

   ```bash
   git clone https://github.com/your-username/php-dev-docker.git
   ```

2. Change into the cloned repository directory:

   ```bash
   cd php-dev-docker
   ```

3. Build the Docker image:

   ```bash
   docker build -t php-dev .
   ```

4. Run a container from the image:

   ```bash
   docker run -d -p 8080:80 --name my-php-dev php-dev
   ```

   This will start a container named `my-php-dev` and bind port 8080 of the host to port 80 of the container. You can change the port mapping according to your requirements.

5. Open your browser and visit `http://localhost:8080` to see the PHP info page.

## Debugging with Xdebug

To enable debugging with Xdebug, you need to configure your IDE or editor accordingly. Here's an example configuration for Visual Studio Code:

1. Install the [PHP Debug](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug) extension.

2. Open the project folder in Visual Studio Code.

3. Create a file named `.vscode/launch.json` with the following contents:

   ```json
   {
     "version": "0.2.0",
     "configurations": [
       {
         "name": "Listen for Xdebug",
         "type": "php",
         "request": "launch",
         "port": 9000,
         "log": true,
         "pathMappings": {
           "/var/www/html": "${workspaceFolder}"
         }
       }
     ]
   }
   ```

4. Set breakpoints in your PHP code.

5. Start the container in debug mode:

   ```bash
   docker run -d -p 8080:80 -p 9000:9000 --name my-php-dev php-dev
   ```

6. Start the debugging session in Visual Studio Code by clicking on the "Run and Debug" button or using the `F5` key.

Now, when you access your PHP application in the browser, Visual Studio Code will pause at the breakpoints, allowing you to step through the code and inspect variables.

## Customization

You can customize the Dockerfile and PHP configuration files according to your specific requirements. Feel free to modify them to suit your needs.

## License

This project is licensed under the [MIT License](LICENSE).

## Contributions

Contributions to this project are welcome. Feel free to open issues or submit pull requests to enhance the Docker image or add new features.