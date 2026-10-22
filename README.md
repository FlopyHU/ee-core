# EE-Core (Electrical Engineering Math & Signal Engine)

![C++17](https://img.shields.io/badge/C%2B%2B-17-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Build](https://img.shields.io/badge/build-header--only-orange.svg)

An open-source, header-only C++17 library and interactive web engine built for electrical engineering calculations: matrix solvers (nodal analysis $Ax = b$), RLC complex impedance, and DSP signal simulation.

🌐 **Live Web Application:** [https://flopyhu.github.io/ee-core/](https://flopyhu.github.io/ee-core/)

---

## 🚀 Features

* **Circuit Engine:** Complex impedance calculations for series/parallel RLC circuits, phasor angles, and cutoff frequencies.
* **Matrix Engine:** High-performance Gaussian Elimination with partial pivoting for linear circuit Nodal Analysis ($Ax = b$).
* **Signal Engine (DSP):** Sine wave generation, RMS voltage/current calculation, and interactive time-domain/frequency visualization.
* **Zero Dependencies:** Pure C++17 standard library (`<complex>`, `<vector>`, `<cmath>`). Header-only design.

---

## 💻 C++ Usage Example

Just include `include/ee_core.hpp` in your C++ project:

```cpp
#include <iostream>
#include "ee_core.hpp"

int main() {
    // Calculate Series RLC Impedance
    auto Z = ee::Circuit::rlcSeries(100.0, 0.01, 0.000001, 1000.0);
    std::cout << "Z: " << Z.real() << " + j(" << Z.imag() << ") Ohm\n";
    return 0;
}
