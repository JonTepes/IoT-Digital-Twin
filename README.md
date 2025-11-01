# Automated Model Factory and Digital Twin

![Factory Digital Twin Overview](images/factory-overview.png)

This project showcases a fully functional automated model factory and its corresponding real-time digital twin. The system is designed for visualizing and controlling physical manufacturing processes through a dynamic 3D interface. Communication between the physical hardware (ESP32 microcontrollers), the server, and the digital twin is handled seamlessly via MQTT.

## Description

The core of this project is a physical model of a production line, mirrored by a virtual replica. This dual setup allows users to monitor machine operations, execute various automation programs, and even manually control individual components like cranes and conveyors. The digital twin serves as a safe, virtual environment for testing, optimizing, and monitoring factory processes before deploying changes to the physical hardware.

## Features

*   **Real-time Visualization:** A 3D representation of the factory using Three.js that accurately mirrors the state of the physical machines.
*   **MQTT Integration:** Seamless, real-time communication between the digital twin, the Node.js server, and physical devices via the MQTT protocol.
*   **Automation Programs:** Support for various automation cycles (e.g., `BasicCycle`, `ColorSortingCycle`) that can be selected and executed through the user interface.
*   **Manual Control:** The ability to manually operate individual machines (e.g., conveyors, cranes) through an interactive control panel in the digital twin.
*   **Dynamic Layout:** Add, move, and save the layout of machines within the 3D scene.
*   **Color Sensing:** The physical factory can detect the color of blocks on the conveyor and sort them accordingly.

## Project Structure

*   `server.js`: The main Node.js server that manages the web server, Socket.IO, and MQTT communication.
*   `FactoryAutomation.js`: Contains the core factory automation logic, manages system states, and delegates tasks to the automation programs.
*   `config.js`: Configuration file for the MQTT broker, server port, and camera URL.
*   `digital_twin/`: Contains the files for the 3D visualization of the digital twin (HTML, JavaScript, 3D models).
    *   `digital_twin/main.js`: The main Three.js logic for rendering the scene, handling user interactions, and connecting to the server.
    *   `digital_twin/FactoryManager.js`: Manages the loading and updating of 3D machine models.
    *   `digital_twin/models/`: Contains the 3D models of the machines (GLB format).
*   `automation_programs/`: Contains the different automation programs.
    *   `automation_programs/BasicCycle.js`: A basic automation cycle.
    *   `automation_programs/ColorSortingCycle.js`: An automation cycle for sorting colored blocks.
*   `ArduinoCode/`: Contains the code for the ESP32 microcontrollers that control the physical machines.

## Automation Programs

*   **BasicCycle:** A fundamental cycle that includes feeding a block onto a conveyor, moving it to a pickup point, retrieval by a crane, and placing it at a designated location.
*   **ColorSortingCycle:** A more advanced cycle that involves detecting the color of a block (blue, yellow, unknown) and sorting the blocks to different drop-off locations based on the detected color.

## Technologies

*   **Backend:** Node.js, Express, MQTT.js, Socket.IO
*   **Frontend:** HTML, CSS, JavaScript, Three.js, Socket.IO client
*   **3D Models:** GLB format
*   **Communication:** MQTT
*   **Physical Control:** ESP32-C3 Supermini (code is in `ArduinoCode/`)
