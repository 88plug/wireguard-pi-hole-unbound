# Wireguard - Pi-hole - Unbound: All-In-One Network Security and Privacy Solution

## Overview

This repository provides an all-in-one solution for network security and privacy. It uses Pi-hole with Unbound for DNS-level ad-blocking and DNSSEC validation, along with WireGuard via WG-Easy for a fast and secure VPN. All services are containerized using Docker for easy deployment and management.

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Prerequisites](#prerequisites)
4. [Getting Started](#getting-started)
    1. [Installation](#installation)
    2. [Configuration](#configuration)

## Features

- **Pi-hole**: DNS sinkhole that protects your devices from unwanted content, without installing any client-side software.
- **Unbound**: A secure, validating, recursive, and caching DNS resolver with support for DNSSEC.
- **WireGuard via WG-Easy**: A fast and modern VPN that uses state-of-the-art cryptography.

## Prerequisites

- Docker and Docker Compose installed.
- Basic understanding of DNS, Docker, and VPN concepts.
- A machine with a static IP address for hosting the services.

## Getting Started

### Installation

1. **Clone the Repository**

    ```bash
    git clone https://github.com/wireguard-pi-hole-unbound
    ```

2. **Navigate to the Project Directory**

    ```bash
    cd wireguard-pi-hole-unbound
    ```

3. **Update Essential Variables**

    Before deploying the services, you must update the following essential environment variables in the `docker-compose.yml` file:

    - **WG_HOST**: Replace with your public IP address.
    - **PASSWORD**: Replace with a secure password.
    - **TZ**: Timezone for the Pi-hole container. Use the "Area/Location" format (e.g., `America/New_York`, `Europe/London`, `Asia/Tokyo`, `Australia/Sydney`, `Africa/Johannesburg`, or `UTC`).
    - **WEBPASSWORD**: Password for accessing the Pi-hole web interface.

4. **Deploy the Services**

    ```bash
    docker-compose up -d
    ```

### Configuration

#### Pi-hole and Unbound

Both are bundled in a single container. Configuration files for Pi-hole are located in the Docker volume `etc_pihole-unbound`. Pi-hole's web interface can be accessed via port 80 or 443, and it listens for DNS queries on port 53.

#### WG-Easy

Configuration files for WG-Easy can be found under `~/.wg-easy`.
