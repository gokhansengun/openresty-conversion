FROM openresty/openresty:1.21.4.1-3-buster

# Add nginx.conf to container
COPY --chown=nobody:0 nginx.conf /usr/local/openresty/nginx/conf/nginx.conf
COPY --chown=nobody:0 start.sh /app/start.sh

# set workdir
WORKDIR /app

# permissions and nginx user for tightened security
RUN chown -R nobody:0 /app && chmod -R 755 /app && \
        chown -R nobody:0 /var/cache/nginx && \
        chown -R nobody:0 /var/log/nginx && \
        chmod -R 755 /var/log/nginx; \
        chown -R nobody:0 /etc/nginx/conf.d
RUN touch /var/run/nginx.pid && chown -R nobody:0 /var/run/nginx.pid

# # Uncomment to keep the nginx logs inside the container - Leave commented for logging to stdout and stderr
# RUN mkdir -p /var/log/nginx
# RUN unlink /var/log/nginx/access.log \
#     && unlink /var/log/nginx/error.log \
#     && touch /var/log/nginx/access.log \
#     && touch /var/log/nginx/error.log \
#     && chown nginx /var/log/nginx/*log \
#     && chmod 644 /var/log/nginx/*log
