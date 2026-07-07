# Netbox_Automations
Automations designed to make Netbox more useful

## Overview
1. Netbox sends new device info to container
2. Docker container processes the info and outputs JSON
3. Termix receives the JSON via REST API, creates new SSH connection

## Steps to Build
### Netbox Event Rules
Build a Netbox event rule to either send the data via webhook or custom script.

### Custom Container
Build a custom Docker container that intakes the device info from Netbox, validates the input, and outputs JSON to Termix (or other SSH connector)

### Termix
Termix receives the info from the custom container and creates a new SSH connection. Will also build support for Tabby, Wave Terminal, Termius, and basic CSV or JSON list outputs. For customizability :)