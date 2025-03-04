FROM php:8.4-cli

# Install system dependencies and SQLite extensions
RUN apt-get update && apt-get install -y --no-install-recommends \
    sqlite3 \
    libsqlite3-dev \
    git \
    && docker-php-ext-install pdo pdo_sqlite \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Install Composer manually
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set working directory
WORKDIR /var/www/html

# Copy project files
COPY . .

# Create SQLite database directory and file
RUN mkdir -p database && touch database/database.sqlite && chmod 777 database/database.sqlite

# Install PHP dependencies using Composer
RUN composer install --no-dev --optimize-autoloader

# Expose port (if running a PHP server)
EXPOSE 8000

# Default command: Run built-in PHP server
CMD ["php", "-S", "0.0.0.0:8000", "-t", "public"]
