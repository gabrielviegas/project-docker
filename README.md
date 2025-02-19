# Docker Container Monitoring with Discord Webhook


## Overview
This script monitors Docker container events and sends a notification to a Discord webhook whenever a container is stopped.

## Features
- **Detects when a container is stopped (die event)
- **Sends a notification to a Discord webhook with the container ID, name, and timestamp
- **Uses the Docker SDK for Python

## Requirements

Ensure your homelab environment is properly configured before running the script.

## Prerequisites
Install the necessary dependencies on your Ubuntu system:

- **sudo apt-get update && sudo apt-get install -y python3 nginx

## Set Up a Python Virtual Environment

It is recommended to use a virtual environment to run the script:

- **python3 -m venv .venv
- **source .venv/bin/activate

## Install Dependencies
Inside the virtual environment, install the required Python package:
- **pip install docker requests

## Configuration

- **Ensure Docker is installed and the Docker daemon is running with the remote API enabled (tcp://127.0.0.1:2375).

- **Replace the webhook_url variable in the script with your actual Discord webhook URL.

- **Run the script:

- **python3 events.py

## Troubleshooting

If you encounter permission issues, run the script with sudo or add your user to the docker group:

- **sudo usermod -aG docker $USER
- **newgrp docker

- **Ensure Docker's remote API is enabled by configuring /etc/docker/daemon.json:

{
  "hosts": ["unix:///var/run/docker.sock", "tcp://127.0.0.1:2375"]
}

Then restart Docker:

- **sudo systemctl restart docker

## Notes

- **The script continuously listens for container stop events.

- **Ensure your Discord webhook is correctly configured.

## License

This project is licensed under the MIT License.
