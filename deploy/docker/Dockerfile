# First stage: Generate Nuxt app
FROM alpine:3.18

# Install necessary tools and dependencies
RUN apk add --no-cache git curl bash gpg sudo

# Set the argument for user id and group id
ARG USER_ID=1000
ARG GROUP_ID=1000
RUN mkdir /home/vscode/app
# Create a new group using the provided group id and create a new user 'vscode' with the provided user id in that group
RUN addgroup -g $GROUP_ID vscode \
    && adduser -D -u ${USER_ID} -G vscode vscode \
    && echo "vscode ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/vscode \
    && chmod 0440 /etc/sudoers.d/vscode \
    && chown -R vscode:vscode /home/vscode

# switch to non root user
USER vscode
WORKDIR /home/vscode/app

CMD ["tail", "-f", "/dev/null"]
