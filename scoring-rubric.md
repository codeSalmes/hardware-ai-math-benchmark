# LLM Hardware Evaluation Rubric

When grading AI models on hardware engineering math, I use the following strict criteria to prevent rewarding "hallucinated logic" (getting the right answer by accident).

- **1.0 (Perfect):** Correct OVR8 formula, correct 3-bit fraction rounding, accurate math error calculation, correct error stacking (+2.5%), and correctly identifies that the connection will FAIL due to exceeding the 3% limit.
- **0.89 (Minor Error):** Correct OVR8 formula and hex value, but fails to stack the HSI tolerance (only calculates the math error) OR gets the error stacking right but miscalculates the fraction rounding slightly.
- **0.40 (Major Logic Flaw):** Uses the OVR16 formula by mistake, or forgets that OVR8 uses a 3-bit fraction (resulting in a wrong hex value), even if the final conclusion is correct.
- **0.0 (Hallucination):** Completely wrong formula, wrong math, or confidently states the connection is fine despite the math showing otherwise.
