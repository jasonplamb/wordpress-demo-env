# Pilw.io Docker Conference - Demo #2

This example builds upon the first ([https://github.com/jasonplamb/wordpress-demo](https://github.com/jasonplamb/wordpress-demo)) however, with an example of .env (environment variable) file usage.

Again, this is primarily used as a **development** environment and not intended for production deployment.

## Usage

 - Clone this repository using Git to a folder of your choice

    git clone https://github.com/jasonplamb/wordpress-demo.git wordpress-demo

 - Change into the folder created during the clone

    cd wordpress-demo

 - Create a .env file based on the .env.dist file provided. You may wish to alter the values for usernames/passwords, etc to personal taste. Remember: .env files themselves should NEVER be placed in source control.

    cp .env.dist .env

 - Bring up the containers

    docker-compose up

 - If you DON'T want to view all the log files flashing past, you could also use the following variant of the docker-compose up command (-d stands for 'detached' mode)

    docker-compose up -d

 - If you opted for the previous example, using the -d option you can still view the log files using the following command and it's variants

    docker-compose logs service-name

	NOTE: service-name is optional. If you opt to leave it out, it will show you the log 		   files for ALL services. Alternatively, if you wish to view the logs for individual services you can substitute service-name for the service defined in docker-compose.yml. For example:

    docker-compose logs wordpress

	You can also view the logs for multiple services

    docker-compose logs wordpress mariadb

	By default the docker-compose logs command will only show previously generated logs. If you wish to keep an eye on things you can 'follow' the logs using the -f option. For example:

    docker-compose logs -f

    docker-compose logs -f wordpress

    docker-compose logs -f wordpress mariadb

## Additional Notes

 - You can view the environment variable defaults passed through to your containers by viewing the contents of .env.

 - You can view the docker-compose.yml file to view how the various environment variables have been used along with their syntax: ${VARIABLE_NAME}

 - If you reviewed the previous example I posted, you may notice that I removed the PHPMyAdmin username/password environment variables. This was done purposefully. By removing them, PHPMyAdmin will now prompt you for a DB, Username/Password combination whereas previously you would have been logged straight in, which is an obvious security risk.