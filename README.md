# Simple_TLS - Go-Back-N Protocol Implementation

A Python implementation of the Go-Back-N (GBN) reliable data transfer protocol, demonstrating reliable file transfer over unreliable UDP connections.

## Overview

This project implements the Go-Back-N protocol, which is a sliding window protocol that provides reliable data transfer over unreliable network connections. It's commonly used in computer networks to ensure data integrity and delivery.

## Features

- **Go-Back-N Protocol**: Implements the complete GBN sender and receiver
- **Reliable File Transfer**: Supports reliable transfer of image files over UDP
- **Error Handling**: Includes checksum verification and packet loss simulation
- **Configurable Parameters**: Adjustable window size, timeout, and loss rate
- **Real-time Monitoring**: Console output showing packet transmission and acknowledgment

## Project Structure

```
├── gbn.py              # Core GBN protocol implementation
├── gbn_client.py       # GBN sender client
├── gbn_server.py       # GBN receiver server
├── client/             # Client directory for source files
│   └── data.jpg        # Sample image file to transfer
└── server/             # Server directory for received files
```

## How It Works

### Go-Back-N Protocol
- **Sender**: Maintains a sliding window of unacknowledged packets
- **Receiver**: Only accepts packets in order, discarding out-of-order packets
- **Error Recovery**: Sender retransmits all unacknowledged packets on timeout
- **Flow Control**: Window-based flow control prevents overwhelming the receiver

### Key Components

1. **GBNSender Class**: Handles packet transmission, acknowledgment waiting, and timeout retransmission
2. **GBNReceiver Class**: Manages packet reception, acknowledgment sending, and data assembly
3. **Checksum Verification**: Ensures data integrity during transmission
4. **Packet Structure**: Structured packets with sequence numbers, flags, and checksums

## Usage

### Prerequisites
- Python 3.x
- No external dependencies required

### Running the Application

1. **Start the Server** (Receiver):
   ```bash
   python gbn_server.py
   ```

2. **Start the Client** (Sender):
   ```bash
   python gbn_client.py
   ```

### Configuration

You can modify the following parameters in `gbn.py`:
- `WINDOW_SIZE`: Number of unacknowledged packets allowed (default: 3)
- `TIMEOUT`: Timeout duration in seconds (default: 10)
- `LOSS_RATE`: Simulated packet loss rate (default: 0.1)
- `BUFFER_SIZE`: UDP buffer size (default: 4096)

## Protocol Details

### Packet Format
- **Data Packet**: `[Sequence Number][Flag][Checksum][Data]`
- **ACK Packet**: `[ACK Sequence][Expected Sequence]`

### State Machine
- **Sender States**: Sending, Waiting for ACK, Timeout Recovery
- **Receiver States**: Waiting for Data, Processing, Sending ACK

## Educational Value

This implementation is excellent for:
- Learning about reliable data transfer protocols
- Understanding sliding window mechanisms
- Studying error detection and recovery
- Network protocol implementation practice

## License

This project is open source and available under the MIT License.

## Contributing

Feel free to submit issues, feature requests, or pull requests to improve this implementation.

## Author

Originally implemented by ZiHuan Wang (2018)
Updated and maintained by the community
