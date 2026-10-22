# EE-Core (Ultimate Engineering Engine)

![C++17](https://img.shields.io/badge/C%2B%2B-17-blue.svg)
![HTML5/JS](https://img.shields.io/badge/Web_Engine-JS%20%7C%20Math.js-yellow.svg)
![License](https://img.shields.io/badge/license-Open_Source-green.svg)

An open-source, dual-architecture engineering toolbox. It features a high-performance, header-only C++17 core library for embedded/native tasks, and a fully interactive, browser-based Web Engine for electrical engineering, signals, and control systems.

Nyílt forráskódú, kettős architektúrájú mérnöki eszköztár. Tartalmaz egy letölthető C++17 alapkönyvtárat, valamint egy teljesen interaktív, böngészőből futtatható vizuális Web Engine-t villamosmérnöki, jelfeldolgozási és irányítástechnikai szimulációkhoz.

🌐 **Live Web Application:** [https://flopyhu.github.io/ee-core/](https://flopyhu.github.io/ee-core/)

---

## 📖 The Story Behind the Project (Miért készült?)

**[HU]** Azért hoztam létre ezt a projektet, mert szükségem volt egyetlen központi helyre, ahol az egyetemi tanulmányaimhoz és a hobbijaimhoz köthető összes számítást és szimulációt elérem. Őszinte leszek: jó néhány tárgyból bukásra állok, így muszáj volt egy kicsit gyakorolnom a kódolást. Mivel programozni tudok, a matematikai és mérnöki motort tiszta C++-ban írtam meg (`ee_core.hpp`). A webes felület (HTML/JS) kódolásához nem tagadom, AI-t használtam, mivel a webfejlesztéshez nem értek – viszont a mögötte álló mérnöki logikát, az architektúra felépítését és a funkciók tervezését teljes egészében én raktam össze. 

**[EN]** I created this project because I needed a single hub for all the calculations related to my university studies and engineering hobbies. I'll be honest: I'm currently failing a few subjects, so I needed a good excuse to practice coding. Since I actually know how to program, I wrote the core math and engineering engine in pure C++. I won't deny that I used AI to help write the HTML/JS web interface because frontend development isn't my area of expertise, but the underlying engineering logic, architecture, and feature concepts are entirely my own.

---

## 🚀 The Web Engine (Böngészős Felület)

The `docs/index.html` file hosts a massive, fully client-side engineering calculator and simulator powered by Math.js, Chart.js, and KaTeX.

* 🎛️ **Circuit & Filter Builder:** Visual RLC filter topology builder with real-time transfer function rendering and oscilloscope simulation (Timebase zoom, noise injection).
* ⚡ **Electrical Engineering:** AC Power triangle (S, P, Q) calculator and DC Ohm's Law solver.
* 🧮 **Complex Matrix Algebra:** Nodal analysis solver, determinant, inverse, and transpose for complex matrices.
* 🎚️ **Control Systems:** Interactive PID controller simulator with real-time step response and overshoot visualization.
* 💻 **Digital Logic:** Live Hexadecimal / Binary / Decimal converter for memory addresses and EEPROM/ECU hex dumps.
* ⚙️ **Machines:** Three-phase asynchronous motor synchronous speed and slip calculator.
* 🔊 **Physics & Acoustics:** Kinematics equations and Helmholtz (Bass-Reflex L-port) physical length calculator.

---

## 💻 C++ Core Usage (Natív C++ Könyvtár)

For hardware or backend tasks, just include the header-only `include/ee_core.hpp` in your C++ project. Zero external dependencies.
Saját C++ vagy mikrokontrolleres projektekhez csak húzd be az `ee_core.hpp` fájlt.

```cpp
#include <iostream>
#include "ee_core.hpp"

int main() {
    // 1. Calculate Series RLC Impedance
    auto Z = ee::Circuit::rlcSeries(100.0, 0.01, 0.000001, 1000.0);
    std::cout << "Z: " << Z.real() << " + j(" << Z.imag() << ") Ohm\n";

    // 2. Solve Nodal Voltage System (Ax = b)
    ee::Matrix A(2, 2);
    A.data[0][0] = 10; A.data[0][1] = -5;
    A.data[1][0] = -5; A.data[1][1] = 15;
    std::vector<double> b = { 12.0, 0.0 };

    std::vector<double> v = ee::Matrix::solveLinearSystem(A, b);
    std::cout << "V1 = " << v[0] << "V, V2 = " << v[1] << "V\n";

    return 0;
}

```

📜 License & Usage Terms (Licenc és Felhasználás)
Copyright (c) 2026 Flopy (NJE Engineering)

This project is open-source. Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to use, copy, modify, merge, publish, distribute, and/or sublicense copies of the Software, subject to the following strict condition:

Attribution Requirement: You must explicitly credit the original author (Flopy) in your source code, project documentation, or website if you use, modify, or integrate any part of this project.

[HU] Felhasználási feltételek (Röviden):
A projekt teljesen nyílt forráskódú. Bárki szabadon felhasználhatja, módosíthatja vagy beépítheti a saját szoftverébe, egyetlen szigorú feltétellel: az eredeti szerzőt (Flopy) egyértelműen meg kell említeni a forráskódban, a projekt leírásában vagy a weboldalon!
