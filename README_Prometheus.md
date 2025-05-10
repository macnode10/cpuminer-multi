# Prometheus: Add README for cpuminer-multi

## Project Overview

CPUMiner-Multi is a high-performance, multi-threaded CPU cryptocurrency mining software designed to support a wide range of mining algorithms. It is a versatile fork of the original CPUMiner, optimized for mining various cryptocurrencies across different platforms.

### Key Features
- Support for multiple cryptocurrency mining algorithms, including:
  * Scrypt (for Litecoin, Dogecoin, Feathercoin)
  * SHA256d (for Bitcoin, Peercoin)
  * X11, X13, X14, X15 (for various altcoins)
  * CryptoNight (for Bytecoin, Monero)
  * And many more

### Benefits
- Cross-platform compatibility (Linux, Windows, macOS)
- Multi-threaded performance optimization
- Supports various CPU architectures (x86, x86-64, ARM)
- Runtime instruction set detection (SSE2, AVX, AVX2)
- Flexible proxy support for mining connections
- Open-source and actively maintained

The miner is particularly useful for cryptocurrency enthusiasts and miners looking for a flexible, efficient CPU mining solution that supports a broad range of coins and algorithms.

## Getting Started, Installation, and Setup

### Prerequisites

Before installing CPUMiner-Multi, ensure you have the following dependencies:
- libcurl (development package)
- OpenSSL (development package)
- GCC or Clang compiler
- autoconf, automake, and libtool (for build process)

### Installation

#### Linux/Unix Installation

1. Clone the repository:
```bash
git clone https://github.com/LucasJones/cpuminer-multi
cd cpuminer-multi
```

2. Prepare the build environment:
```bash
./autogen.sh  # Only needed if building from git repository
```

3. Configure the build:
```bash
./configure CFLAGS="-march=native"  # Optimizes for your specific CPU architecture
```

4. Compile the miner:
```bash
make
```

#### Windows Installation (MinGW)

1. Install:
- MinGW and MSYS Developer Tool Kit
- pthreads-w64 (for MinGW-w64)
- libcurl development package
- OpenSSL development package

2. In the MSYS shell, run:
```bash
./autogen.sh  # Only needed if building from git repository
LIBCURL="-lcurldll" ./configure CFLAGS="-march=native"
make
```

### Quick Start

After installation, run the miner with:
```bash
./minerd --help  # View available options
```

Example mining command:
```bash
./minerd -a scrypt -o stratum+tcp://pool.example.com:3333 -u username -p password
```

### Platform-Specific Notes

#### ARM Architecture
- No runtime CPU detection
- Add `-mfpu=neon` to CFLAGS to use NEON instructions

#### x86/x86-64 Architecture
- Supports SSE2, AVX, AVX2, and XOP instructions
- Checks for instruction set support at runtime
- OS-level AVX support requirements vary by platform

### Configuration

An example configuration file is provided as `example-cfg.json`. You can customize mining parameters, pool settings, and algorithm preferences.

### Troubleshooting

- Ensure all dependencies are installed
- Check that your system meets the minimum requirements
- Use the `--help` option for detailed usage instructions
- Verify network and pool connectivity