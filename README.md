# Docker-PHP

Welcome to Docker-PHP, your starter kit for PHP development facilitated by Docker. This project provides integrated support for key technologies: MySQL, Nginx, and Redis, creating a robust environment for both development and production needs.

## Initial Configuration

To get started, you need to set up your environment variables. This is done by creating two distinct files in the root directory: `.env` and `.env.local`. These files are essential for differentiating your development settings from production settings.

The `.env` file is for your production environment. Populate it with the following variables:

```plaintext
MYSQL_PORT=3306
MYSQL_DATABASE=freshroots
MYSQL_USER=fr_admin
MYSQL_PASSWORD=user_password
MYSQL_ROOT_PASSWORD=root_password
REDIS_PORT=6379
```

For your development environment, create a `.env.local` file with these variables, plus additional settings for development:

```plaintext
MYSQL_PORT=3306
MYSQL_DATABASE=freshroots
MYSQL_USER=fr_admin
MYSQL_PASSWORD=user_password
MYSQL_ROOT_PASSWORD=root_password
REDIS_PORT=6379
BUILD_TARGET=app_dev
XDEBUG_MODE=debug
```

To proceed with the installation of PHP dependencies, navigate to the /app directory and execute the following command:

```bash
compose install --ignore-platform-reqs
```

This will install the necessary PHP dependencies, bypassing specific platform requirements.## Launching the Project

To bring your project to life, execute the following command:

```bash
docker compose up -d
```

This command launches the project in production mode. If you wish to operate in development mode, use this alternative command:

```bash
docker compose -f docker-compose.dev.yml --env-file .env.local up -d
```

### Customization and Repository Initialization

Feel free to tailor the project to your needs. This includes the option to remove unnecessary services, modify or remove the `.gitignore` and `README.md` files, and most importantly, to initialize a new Git repository. To start fresh with Git, first delete the existing `.git` folder, then run `git init`.

## Contributing

We welcome contributions to this project! Whether it's through submitting bug reports, proposing improvements, or contributing code, your input is valuable. To get started, please fork the repository, create a feature branch, and submit your pull request for review.

## License

This project is released under the MIT License. This means it is free to use, modify, and distribute, both for private and commercial purposes.

## Contact

For any queries or discussions regarding this project, feel free to contact us. You can reach out to me at [aryalaashaya@gmail.com](mailto:aryalaashaya@gmail.com). We're always open to feedback and new ideas!
