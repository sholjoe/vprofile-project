# Use nginx as base image
FROM nginx

# Set labels
LABEL "Project"="Vprofile"
LABEL "Author"="Olusola"

# Remove the default nginx configuration file
RUN rm -rf /etc/nginx/conf.d/default.conf

# Copy your nginx configuration file
COPY nginxvproapp.conf /etc/nginx/conf.d/vproapp.conf
