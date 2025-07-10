# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a GPU-accelerated particle morphing visualization using Three.js and WebGL. The application demonstrates advanced 3D graphics techniques with 20,000 particles morphing between various shapes including a detailed Angkor Wat temple model.

## Development Setup

This is a **vanilla JavaScript project** with no build system:
- No dependencies to install
- No build commands required
- Simply open `particle_morph.html` in a modern web browser
- Uses Three.js v0.162.0 loaded via CDN

## Architecture

The entire application is contained in a single file: `particle_morph.html`

### Key Components:

1. **Particle System** - GPU-accelerated particles with custom GLSL shaders
2. **Shape Generators** - Functions that create particle positions for:
   - Sphere (Fibonacci distribution)
   - Bird (wings, body, head)
   - Face (human features)
   - Tree (recursive branches)
   - Angkor Wat (detailed Khmer architecture)
3. **Post-Processing Pipeline** - Bloom, motion blur, gamma correction
4. **Interactive Controls** - Particle size, rotation, color, effects

### Shader System:

- **Vertex Shader**: Handles morphing interpolation, size attenuation, floating animation
- **Fragment Shader**: Creates circular particles with soft edges and glow

### Important Implementation Details:

- All particle calculations happen on GPU for performance
- Morphing uses vertex shader interpolation between position buffers
- Post-processing uses Three.js EffectComposer with multiple passes
- The Angkor Wat model is the most complex, featuring authentic architectural details

## Common Tasks

Since this is a single-file project with no build system:
- **To test changes**: Refresh the browser
- **To debug**: Use browser DevTools console
- **To add new shapes**: Create a new generator function following the existing pattern
- **To modify shaders**: Edit the GLSL strings in the ShaderMaterial definition

## Performance Considerations

- The app uses 20,000 particles by default
- All transformations are GPU-accelerated
- Avoid CPU-side particle manipulation in the render loop
- Use buffer attributes for any per-particle data