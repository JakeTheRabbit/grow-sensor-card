You're absolutely right. Here's the README with PROPERLY closed code blocks - I'll format it exactly as it should appear in the actual file:

# Grow Sensor Card

[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg)](https://github.com/custom-components/hacs)

A custom card for Home Assistant that displays grow room environmental data in an intuitive dashboard format. Perfect for monitoring grow room conditions including temperature, humidity, VPD, CO2, and air quality metrics.

## Features

- Temperature readings from multiple sensors
- Humidity levels across different locations
- VPD (Vapor Pressure Deficit) monitoring
- CO2 concentration tracking
- Air quality measurements (VOC, NOx, PM levels)
- Visual trend indicators
- Tabbed interface
- Responsive grid layout

## Installation

### HACS (Recommended)

1. Ensure [HACS](https://hacs.xyz/) is installed
2. Add this repository to HACS:
    - Click HACS in your Home Assistant sidebar
    - Go to "Frontend"
    - Click menu (3 dots) in top right
    - Select "Custom repositories"
    - Add `https://github.com/legacygrow/grow-sensor-card`
    - Select "Lovelace" category
3. Install "Grow Sensor Card"
4. Refresh your browser cache

### Manual Installation

1. Download `grow-sensor-card.js`
2. Copy to `config/www` directory
3. Add to `configuration.yaml`:

```yaml
lovelace:
  resources:
    - url: /local/grow-sensor-card.js
      type: module
```

## Configuration

Add to your dashboard:

```yaml
type: 'custom:grow-sensor-card'
entities:
  temperature:
    left_back: sensor.left_back_temperature
    middle_canopy: sensor.middle_canopy_temperature
    left_front: sensor.left_front_temperature
    right_back: sensor.right_back_temperature
  humidity:
    f1_scd41: sensor.f1_scd41_humidity
    middle: sensor.middle_humidity
    left: sensor.left_humidity
    hepa: sensor.hepa_humidity
  vpd:
    f1_scd41: sensor.f1_scd41_vpd
    middle: sensor.middle_vpd
    left: sensor.left_vpd
    right: sensor.right_vpd
  co2:
    f1_scd41: sensor.f1_scd41_co2
    middle: sensor.middle_co2
    left: sensor.left_co2
  air_quality:
    voc: sensor.voc
    nox: sensor.nox
    pm25: sensor.pm25
thresholds:
  temperature: 24
  humidity: 75
  vpd: 0.8
  co2: 1200
```

### Options

| Option | Type | Required | Description |
|--------|------|----------|-------------|
| entities | object | yes | Your sensor entities |
| thresholds | object | yes | Alert thresholds |

### Entity Structure
Each sensor category needs entity IDs:

```yaml
temperature:
  location_name: sensor.entity_id
humidity:
  location_name: sensor.entity_id
```

### Thresholds
Set warning levels:

```yaml
thresholds:
  temperature: 24    # °C
  humidity: 75      # %
  vpd: 0.8         # kPa
  co2: 1200        # ppm
```

## Support

- 🌟 Star on GitHub
- 🐛 Report issues
- 🤝 Contribute to development

## License

MIT License

---
Made with 🌱 by [Legacy Grow](https://legacygrow.co.nz)

Let me know if you'd like me to provide just the raw markdown text without any formatting or if you need any adjustments to the content!
