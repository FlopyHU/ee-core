# EE-Core C++ Engine – Usage Guide

**EE-Core** is a *header-only* C++17 library. This means there is no need for complex installations, external dependencies, or linking static/dynamic libraries (DLL, SO). 

Simply copy the `include/ee_core.hpp` file into your project and include it in your code.

---

## 🛠️ 1. Compilation

It works out of the box with any standard C++17 compiler (GCC, Clang, MSVC). To compile a simple `main.cpp` file from the command line:

**GCC (Linux / MinGW Windows):**
```bash
g++ -std=c++17 main.cpp -o ee_program
./ee_program
```

**Clang (macOS / Linux):**
```bash
clang++ -std=c++17 main.cpp -o ee_program
./ee_program
```

---

## ⚡ 2. Electrical Engineering (Circuit & Power)
Calculate complex impedance, RLC networks, and AC/DC power parameters.

```cpp
#include <iostream>
#include "ee_core.hpp"

int main() {
    // 1. Calculate Series RLC Impedance (R=100Ω, L=10mH, C=1uF, f=1kHz)
    auto Z = ee::Circuit::rlcSeries(100.0, 0.01, 0.000001, 1000.0);
    std::cout << "Complex Impedance (Z): " << Z.real() << " + j" << Z.imag() << " Ohm\n";
    
    // 2. RC Filter Cutoff Frequency (Bode)
    double fc = ee::Circuit::rcCutoffFrequency(1000.0, 0.0000001); // 1kΩ, 0.1uF
    std::cout << "RC Cutoff Frequency (-3dB): " << fc << " Hz\n";

    return 0;
}
```

---

## 🧮 3. Matrices & Nodal Analysis (Ax = b)
Solve systems of linear equations for nodal voltage analysis using Gaussian elimination with partial pivoting.

```cpp
#include <iostream>
#include <vector>
#include "ee_core.hpp"

int main() {
    try {
        // Conductance matrix [A] (2x2)
        ee::Matrix A(2, 2);
        A.data[0][0] = 10; A.data[0][1] = -5;
        A.data[1][0] = -5; A.data[1][1] = 15;

        // Source vector [b]
        std::vector<double> b = { 12.0, 0.0 };

        // Solve the linear system
        std::vector<double> voltages = ee::Matrix::solveLinearSystem(A, b);

        std::cout << "Nodal voltages:\n";
        std::cout << "V1 = " << voltages[0] << " V\n";
        std::cout << "V2 = " << voltages[1] << " V\n";
    } 
    catch (const std::exception& e) {
        // Catches singular (determinant = 0) matrix errors gracefully
        std::cerr << "Error: " << e.what() << '\n';
    }

    return 0;
}
```

---

## 🌊 4. Signals & Systems (DSP Engine)
Generate discrete time-domain signals and calculate RMS (Root Mean Square) values.

```cpp
#include <iostream>
#include <vector>
#include "ee_core.hpp"

int main() {
    // Generate a sine wave (5V peak, 50Hz, 0 phase, 100 samples, 1000Hz sample rate)
    std::vector<double> sineWave = ee::SignalEngine::generateSine(5.0, 50.0, 0.0, 100, 1000.0);

    // Calculate RMS voltage
    double v_rms = ee::SignalEngine::calculateRMS(sineWave);
    std::cout << "Generated signal RMS value: " << v_rms << " V\n";

    return 0;
}
```

---

## 🏗️ Namespaces Overview
To keep the codebase clean and modular, all core functions are grouped inside the `ee::` namespace:
* `ee::Circuit` - Electrical engineering, impedance math, AC/DC networks.
* `ee::Matrix` - Linear algebra and nodal network solvers.
* `ee::SignalEngine` - Discrete signals, DSP, and waveform generation.

*All functions are declared as `static`, meaning they can be called directly without instantiating objects from the classes.*
