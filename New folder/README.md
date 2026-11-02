# Voice Effects Plugin

A plugin for Aliucord that adds real-time audio processing to Discord voice calls, allowing you to modify outgoing voice with reverb, pitch shifting, and frequency modulation effects.

## Features

### 🎚️ Pitch Shifting
- Range: -12 to +12 semitones
- Create robotic or cartoon voice effects
- Uses overlap-add algorithm for smooth pitch changes

### 🔊 Frequency Modulation (Ring Modulation)
- Range: 0 to 500 Hz
- Creates metallic or distorted sounds
- Uses LFO-controlled ring modulation

### 🏛️ Reverb
- Mix: 0% to 100%
- Decay: 0.1s to 2.0s
- Includes echo, hall, and room effect presets
- Uses Schroeder's algorithm

### 📦 Presets
Four built-in presets for easy use:
- **None**: No effects
- **Robot**: High pitch + metallic effects
- **Echo**: Simple echo effect
- **Hall**: Large hall simulation

## Installation

### Prerequisites

1. **Aliucord**: Latest version
2. **Discord for Android**: Version 126021 or later
3. **Root Access**: Required for audio backend control

### Installation Steps

1. **Download the Plugin**
   ```bash
   git clone https://github.com/yourusername/voice-effects-plugin.git
   cd voice-effects-plugin
   ```

2. **Build the Plugin**
   ```bash
   ./gradlew assembleDebug
   ```

3. **Locate Plugin Directory**
   - Rooted: `/storage/emulated/0/Aliucord/plugins`
   - Non-rooted: Use Aliucord's plugin manager

4. **Install**
   - Copy `build/outputs/apk/debug/app-debug.apk` to plugins directory
   - Or extract the zip file if provided
   - Reload plugins in Aliucord
   - Enable "Voice Effects"

## Usage

### Basic Controls

1. **Enable/Disable**: Toggle the main switch
2. **Pitch Shift**: Adjust semitones using the seek bar
3. **Frequency Mod**: Adjust Hz using the seek bar
4. **Reverb Mix**: Adjust mix percentage (0-100%)
5. **Reverb Decay**: Adjust decay time (0.1-2.0 seconds)

### Presets

Click the preset spinner to quickly apply:
- **None**: No effects
- **Robot**: For robotic voices
- **Echo**: For echo effects
- **Hall**: For large hall simulations

### Testing

1. Open Discord
2. Join a voice call
3. Enable the plugin
4. Adjust settings
5. Test in a voice channel with another user

## Configuration

### Plugin Settings

All settings are adjustable in real-time:

- **Pitch Shift**: From -12 semitones (very low) to +12 semitones (very high)
- **Frequency Mod**: From 0 Hz (no modulation) to 500 Hz (strong metallic effect)
- **Reverb Mix**: From 0% (dry) to 100% (wet)
- **Reverb Decay**: From 0.1 seconds (short echo) to 2.0 seconds (long hall)

### Presets

Each preset includes optimized settings:

```
Robot:     Pitch=+12, Freq=200, Mix=0%, Decay=0.5
Echo:      Pitch=0,   Freq=0,   Mix=30%, Decay=1.0
Hall:      Pitch=+7,  Freq=50,   Mix=50%, Decay=1.2
```

## Technical Details

### How It Works

1. **Audio Backend**: Forces Discord to use Java audio backend (androidJavaAudio)
2. **PCM Capture**: Intercepts raw PCM data from AudioRecord
3. **DSP Processing**: Applies effects in sequence:
   - Pitch shifter
   - Frequency modulator
   - Reverb
4. **WebRTC Output**: Sends processed audio to Discord

### Performance

- **Latency**: ~10ms (20ms audio buffer)
- **CPU**: Low to moderate
- **Memory**: ~1MB for reverb buffer
- **Sample Rate**: 48kHz
- **Channels**: Mono

## Troubleshooting

### Plugin Not Loading

- ✅ Check plugin directory exists
- ✅ Verify Discord version compatibility
- ✅ Ensure root access (if required)
- ✅ Restart Aliucord after installation

### Audio Not Processed

- ✅ Plugin is enabled
- ✅ Native hook is applied
- ✅ Try restarting Discord
- ✅ Check plugin logs

### Native Library Errors

- ✅ Native library needs recompilation
- ✅ Discord version mismatch
- ✅ Missing system dependencies

## Building

### Requirements

- Android Studio or Gradle
- CMake 3.10+
- JDK 8+

### Build Commands

```bash
# Build debug version
./gradlew assembleDebug

# Build release version
./gradlew assembleRelease

# Install to connected device
./gradlew installDebug

# Run tests
./gradlew test
```

## License

MIT License

Copyright (c) 2024 OpenCode

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

### Code Quality

- Follow Kotlin coding standards
- Write unit tests
- Add documentation
- Ensure compatibility with all supported Discord versions

### Issues

Report bugs and feature requests:
- Create issues in this repository
- Provide detailed reproduction steps
- Include device information and Discord version

## Credits

Special thanks to:
- Discord for their API and audio pipeline
- WebRTC team for the audio backend
- The community for feedback and testing
- Reverse engineering contributors for initial analysis

## Support

For support, issues, or questions:
- Check the documentation
- Create an issue on GitHub
- Join the community (if available)