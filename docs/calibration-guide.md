# Calibration Guide for Rotary Encoder Measurement System

This guide explains how to calibrate your rotary encoder measurement system to ensure accurate distance measurements.

## Why Calibration Is Important

The accuracy of your measurement system depends on:

1. The encoder's resolution (500 PPR in our case)
2. The circumference of the measurement wheel
3. Any mechanical factors like slippage or friction

While we can calculate a theoretical distance based on wheel size and encoder pulses, real-world conditions require calibration for optimal precision.

## Calibration Procedure

### Prerequisites

- A measuring tape or ruler (preferably at least 1 meter long)
- A straight, flat surface for testing
- Your fully assembled measurement system

### Step 1: Initial Setup

1. Power on your measurement system
2. Press the RESET button to zero the measurement
3. Place your measuring wheel at the starting point of your measuring tape

### Step 2: Measure a Known Distance

1. Mark a start position on your material or surface
2. From that position, mark an exact distance (recommend 1000mm/1m for best results)
3. Make sure the measuring tape is parallel to the path the wheel will travel

### Step 3: Record Measurement

1. Move your measuring wheel from the start position to the end position, following a straight line
2. Note the distance displayed on your measurement system
3. Calculate the calibration factor:

```
calibration_factor = actual_distance / measured_distance

Example:
If you moved exactly 1000mm but your display shows 995mm:
calibration_factor = 1000 / 995 = 1.005
```

### Step 4: Update the Calibration Value

Open the `stm32_encoder_interface.ino` file and find the calibration factor setting:

```cpp
// Find this line in your code
float calibrationFactor = 1.0; // Default value

// Change it to your calculated value
float calibrationFactor = 1.005; // Your calibration value
```

### Step 5: Upload and Verify

1. Upload the updated firmware to your STM32
2. Repeat the measurement test
3. The display should now show the correct distance
4. If needed, fine-tune the calibration factor with another iteration

## Fine-Tuning

For even greater precision, you can:

1. Take multiple measurements at different distances
2. Calculate the average calibration factor
3. Check for consistency across different materials and surfaces

## Troubleshooting

### Display Shows Zero or Doesn't Change

- Check encoder connections (A, B signals)
- Verify the wheel is making good contact with the surface
- Check that the encoder shaft is rotating freely

### Inconsistent Measurements

- Look for wheel slippage on the material
- Check for debris on the wheel
- Ensure consistent pressure on the wheel

### Measurements Drift Over Time

- Check for mechanical play in wheel mounting
- Verify encoder mounting is secure
- Consider environmental factors (temperature, humidity)

## Regular Calibration

For best results, perform calibration:

- After initial setup
- Any time you change the measurement wheel
- If you notice a drift in measurement accuracy
- When measuring different types of materials
- After any mechanical maintenance

With proper calibration, your measurement system should achieve accuracy within ±0.1% of the actual distance, which is approximately ±1mm per meter.
