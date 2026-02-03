*This project has been created as part of the 42 curriculum by aakritah.*

## Description
**NetPractice** is a practical networking exercise designed to introduce the fundamentals of computer communication. The primary goal is to configure small-scale networks by correctly setting up IP addresses, subnet masks, and default gateways. The project consists of 10 levels of increasing difficulty, each requiring the user to resolve connection issues within a simulated environment.


## Description
**NetPractice** is a practical exploration into the foundational mechanics of computer networking. This project shifts from theoretical study to hands-on configuration, requiring the resolution of 10 increasingly complex networking levels within a simulated environment. The objective is to engineer functional communication pathways across diverse network topologies by precisely managing IP addresses, subnet masks, and routing logic. By diagnosing connectivity issues through simulation logs, this project builds a deep, intuition-based understanding of how data packets traverse routers and gateways to reach their destination.


## Instructions
### Running the Interface
This project uses a simulated training interface accessible via a web browser.
1. **Extraction**: Download the project files and extract them to your chosen folder.
2. **Execution**: Run the `run.sh` script in your terminal to launch the local web server and open the interface.
3. **Manual Backup**: If the script fails, run `python3 -m http.server 49242` and navigate to `http://localhost:49242` in your browser.
4. **Login**: You must enter your intranet login so the system can identify your specific configuration.

### Exporting and Submission
* **Exporting**: Once a level is successfully completed, use the **[Get my config]** button to download the configuration file.
* **Submission**: You must submit exactly **10 configuration files** (one per level) at the root of your Git repository.
* **Defense**: During evaluation, you will be required to complete three random levels within a limited time without external tools.

## Resources
### Networking Concepts
To complete these levels, the following concepts were studied and applied:
* **TCP/IP Addressing**: Understanding how unique identifiers are assigned to network devices.
* **Subnet Masks**: Defining the boundaries between the network and host portions of an address.
* **Default Gateways**: Configuring the exit point for data packets traveling to external networks.
* **Routers and Switches**: Learning how hardware manages traffic between different subnets.
* **OSI Model Layers**: Reviewing the conceptual layers of data transmission.

### AI Usage
In alignment with the project's AI instructions:
*  Clarify theoretical networking concepts .
*  Verify understanding of subnetting and routing rules.