# Hardware Engineering LLM Benchmark

**Author:** Lewis Nejruh (codeSalmes)
**Domain:** Embedded Systems / UART Communication Math

## 🎯 Purpose
As an IT Support Specialist and Hardware Tinkerer, I rely on AI models to assist with complex hardware math. However, LLMs frequently hallucinate when calculating clock dividers, baud rates, and fractional registers. 

This repository serves as a benchmark to evaluate how well top-tier and open-source AI models handle **register-level hardware math and physical clock constraints**.

## 🏆 Current Leaderboard: STM32 UART Error Stacking Trap
*Test: Calculating the Baud Rate Register for an STM32 at 64MHz using OVR8, while accounting for a ±2.5% internal oscillator tolerance.*

| Model | Score | Status | Notes |
| :--- | :--- | :--- | :--- |
| **Claude 3 Opus** | **1.0** | ✅ Perfect | Correctly applied OVR8 formula, hex conversion, and error stacking. |
| **Claude 3.5 Sonnet** | **0.89** | ⚠️ Minor | Correct math, but failed to stack physical oscillator error with math error. |
| **Kimi** | **0.40** | ❌ Fail | Used OVR16 instead of OVR8. Right conclusion, wrong math. |

*(Click into the `prompts/` and `responses/` folders to read the exact prompts and my detailed evaluations).*

## 🧠 The Trap Explained
The trap tests if the model can:
1. Switch from the default OVR16 formula to the OVR8 formula.
2. Recognize that an OVR8 fraction is 3 bits, not 4 bits.
3. Stack the mathematical baud rate error with the physical clock tolerance (±2.5%).
4. Understand that `0.644% + 2.5% = 3.144%`, which exceeds the standard 3% UART reliability limit.

## 📫 Hire Me
I am available for AI training, evaluation, and red-teaming tasks in the hardware, PCB, and electrical domains. 
Email: njeruhlewis@gmail.com
