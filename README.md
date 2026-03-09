# Haas Inspection Post-Processor Enhanced (v3.5)

Professional-grade G-code optimization and safety engine for Haas CNC machines. This project integrates advanced path smoothing, arc fitting, and rigorous machine safety protocols into the standard Haas inspection post-processor.

## Key Features

### 🚀 Performance & Optimization
- **G-Code Smoothing & Linearization**: Grouped optimization controls for Linearization, Arc Override, and Spline/3D Smoothing.
- **Experimental Arc Fitting**: Sophisticated logic to convert high-density linear paths into smooth G02/G03 arcs, significantly reducing program size and improving machine motion.
- **Helix & Cylinder Fitting**: Advanced geometric recognition for helical and cylindrical toolpaths.
- **Concurrent Tool Positioning**: X and Y positioning moves are executed simultaneously with tool changes where safe, reducing cycle time.
- **Early PCOOL Adjustment**: Forces tool length compensation (G43 H#) immediately after tool changes for enhanced safety and setup verification.

### 🛡️ Safety & Reliability
- **Restart Protection**: Mandatory Z-retract (`G53 Z0`) before any horizontal movement on program restarts, preventing accidental tool collisions.
- **Rotary Axis Safeguards**: Simultaneous rotary rapids with Z-retract protection before indexing. Forced 100% rapid override for predictable rotary performance.
- **WCS Transition Safety**: Overhauled retract logic ensuring absolute safety during Work Coordinate System transitions.
- **Verification Engine**: Real-time geometric verification of all optimizations. If an optimization exceeds defined tolerances, the system automatically restores the original original path.

### 🔍 Inspection Integration
- Full support for Haas Renishaw probing cycles.
- Live connection capabilities for real-time measurement results.
- Enhanced reporting and error handling for critical inspection points.

## Project Structure
- `V3.5_Production_Inspection_11-19-25.cps`: The core Haas Post-Processor configuration.
- `V2_Optimization_Engine.js`: The standalone JavaScript engine responsible for G-code analysis and optimization.

## Installation
1. Place the `.cps` file in your Fusion 360 Post-Processor directory.
2. Ensure the `V2_Optimization_Engine.js` is accessible to the post-processor (configured via CPS properties).
3. Update the `customPostProcessing` property in the CPS to enable the optimization engine.

## Usage
Select the "Haas-Inspection-Post-Pro-Enhanced" post-processor during NC program generation in Fusion 360. Configure optimization levels through the Post Properties menu.

---
**Disclaimer**: Always verify G-code in a simulator (like Haas NC Viewer or Vericut) before running on a live machine. Extreme care was taken in the engineering of these safety features, but the operator remains responsible for final machine safety.
