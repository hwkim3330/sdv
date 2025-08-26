# China SDV Standard Summary - English Version

## SDV Intelligent Connected Vehicle Service Interface Specification
### Version 4 Beta 1

---

## Part 1: Atomic Service API Interface

### Overview
The Atomic Service API provides standardized functional interfaces for application developers to access vehicle features without needing to understand the underlying hardware complexity.

### Key Domains and APIs

#### 1. BCM (Body Control Module) Domain
**Purpose**: Controls vehicle body comfort and convenience features

**Major Services**:
- **BCM_Door**: Door control services
  - `unlock()`: Unlock doors
  - `lock()`: Lock doors
  - `open()`: Open doors
  - `close()`: Close doors
  - `adjustPosition()`: Adjust door position
  
- **BCM_Window**: Window control services
  - `open()`: Open windows
  - `close()`: Close windows
  - `adjustPosition()`: Set window position
  - `lock()`: Lock window operation
  
- **BCM_Seat**: Seat control services
  - `adjustMainXDir()`: Adjust seat forward/backward
  - `adjustBackRestAngle()`: Adjust backrest angle
  - `setHeating()`: Control seat heating
  - `setVentilation()`: Control seat ventilation
  
- **BCM_Light**: Lighting control services
  - `turnOn()`: Turn on lights (brake, turn signal, headlights)
  - `turnOff()`: Turn off lights
  - `setIntensity()`: Adjust light intensity
  
- **BCM_WiperWash**: Wiper and washer services
  - `startWiping()`: Start wipers
  - `stopWiping()`: Stop wipers
  - `startSprayWashing()`: Activate washer fluid spray

#### 2. TMS (Thermal Management System) Domain
**Purpose**: Manages vehicle thermal conditions for comfort and efficiency

**Major Services**:
- **TMS_AC**: Air conditioning services
  - `setTargetTemp()`: Set target cabin temperature
  - `setFanSpeed()`: Adjust fan speed
  - `setAirDirection()`: Control air flow direction
  
- **TMS_Battery**: Battery thermal management
  - `setTargetTemp()`: Set battery target temperature
  - `getCoolantTemp()`: Get coolant temperature
  - `activateCooling()`: Enable battery cooling
  
- **Version 4 Additions** (APIs 4.9.24-4.9.29):
  - `TMS_Radiator.setFlowRate()`: Control radiator flow
  - `TMS_Coolant.getTemperature()`: Monitor coolant temperature
  - `TMS_HeatPump.activate()`: Control heat pump operation

#### 3. VCS (Vehicle Control System) Domain
**Purpose**: Controls vehicle motion and dynamics

**Major Services**:
- **VCS_Gear**: Transmission control
  - `setTarget()`: Set target gear (PARK, REVERSE, NEUTRAL, DRIVE)
  - `getCurrentGear()`: Get current gear position
  
- **VCS_Brake**: Braking system control
  - `setTargetAx()`: Set target deceleration
  - `enableABS()`: Enable anti-lock braking
  - `getBreakPressure()`: Monitor brake pressure
  
- **VCS_Steering**: Steering control
  - `setAngle()`: Set steering angle
  - `enableAssist()`: Enable power steering assist

#### 4. EMS (Energy Management System) Domain
**Purpose**: Manages vehicle energy and power distribution

**Major Services**:
- **EMS_Charging**: Charging control
  - `start()`: Start charging process
  - `stop()`: Stop charging
  - `setChargingPower()`: Set charging rate
  - `getChargingStatus()`: Get charging status
  
- **EMS_HVBatt**: High-voltage battery management
  - `getSOC()`: Get State of Charge
  - `getSOH()`: Get State of Health
  - `getCellVoltages()`: Monitor individual cell voltages
  
- **EMS_PowerDistribution**:
  - `optimize()`: Optimize power distribution
  - `setPowerLimit()`: Set power consumption limits

#### 5. ADAS (Advanced Driver-Assistance Systems) Domain
**Purpose**: Provides intelligent driving assistance features

**Major Services**:
- **ADAS_Perception**: Visual perception services
  - `getTrackObjects()`: Detect vehicles, pedestrians, objects
  - `getLaneline()`: Detect lane markings
  - `getTrafficLight()`: Recognize traffic lights
  - `getParkingSpace()`: Identify parking spaces
  - `getRoadSign()`: Read road signs
  
- **ADAS_Radar**: Radar perception
  - `notifyObjects()`: Report radar-detected objects
  - `getDistance()`: Measure distances to objects
  
- **ADAS_Lidar**: Lidar perception
  - `notifyObjects()`: Report lidar-detected objects
  - `getPointCloud()`: Provide point cloud data
  
- **ADAS_Fusion**: Sensor fusion
  - `getCombinedObjects()`: Get fused sensor results

#### 6. HMI (Human Machine Interface) Domain
**Purpose**: Manages user interaction and information display

**Major Services**:
- **HMI_Display**: Display control
  - `showNotification()`: Display notifications
  - `updateInstrumentCluster()`: Update driver display
  
- **HMI_Audio**: Audio system control
  - `playMedia()`: Play audio content
  - `setVolume()`: Adjust volume
  - `enableVoiceAssistant()`: Activate voice control
  
- **HMI_Navigation**: Navigation services
  - `setDestination()`: Set navigation destination
  - `calculateRoute()`: Calculate optimal route
  - `provideGuidance()`: Provide turn-by-turn guidance

---

## Part 2: Device Abstraction API Interface

### Overview
The Device Abstraction API provides standardized interfaces for controlling hardware devices, enabling hardware independence and vendor flexibility.

### Key Domains and Devices

#### 1. BCM Device Domain
**Actuators**:
- **Actr_DoorLock**: Door lock motor control
  - `lock()`: Engage door locks
  - `unlock()`: Disengage door locks
  
- **Actr_DoubleHallMot**: Window/sunroof motor with Hall sensors
  - `setOper(dir, dutyRat)`: Control motor operation
  - `getPosition()`: Get current position
  
- **Actr_SeatHeatr**: Seat heater control
  - `setLevel()`: Set heating level
  
**Sensors**:
- **Snsr_WinSwt**: Window switch sensor
  - `getStatus()`: Read switch status
  
- **Snsr_SeatOccupied**: Seat occupancy sensor
  - `isOccupied()`: Detect seat occupancy
  
- **Snsr_DoorSts**: Door status sensor
  - `getPosition()`: Get door position

#### 2. TMS Device Domain
**Actuators**:
- **Actr_EWP**: Electric water pump
  - `setSpeed()`: Control pump speed
  
- **Actr_Compressor**: AC compressor
  - `enable()`: Turn on compressor
  - `setOutput()`: Set cooling output
  
**Sensors**:
- **Snsr_Temper**: Temperature sensors
  - `getTemperature()`: Read temperature value
  
- **Snsr_Humidity**: Humidity sensor
  - `getHumidity()`: Read humidity level

#### 3. PWT (Powertrain) Device Domain
**Actuators**:
- **Actr_ChrgElecLock**: Charging port lock
  - `lock()`: Lock charging port
  - `unlock()`: Unlock charging port
  
- **Actr_HvBattCtrl**: High-voltage battery relay control
  - `enable()`: Connect battery
  - `disable()`: Disconnect battery
  
- **Actr_DcdcCtrl**: DC-DC converter control
  - `setOutputVoltage()`: Set conversion voltage
  
**Sensors**:
- **Snsr_AcChrgPortT**: AC charging port temperature
  - `getTemperature()`: Monitor port temperature
  
- **Snsr_DcChrgPortT**: DC charging port temperature
  - `getTemperature()`: Monitor port temperature
  
- **Snsr_HvBattCellInfo**: Battery cell information
  - `getVoltage()`: Read cell voltages
  - `getTemperature()`: Read cell temperatures

#### 4. CHS (Chassis) Device Domain
**Sensors**:
- **Snsr_BrkPedlSwt**: Brake pedal switch
  - `isPressed()`: Detect brake pedal activation
  
- **Snsr_AccPedlPos**: Accelerator pedal position
  - `getPosition()`: Read pedal position
  
- **Snsr_SteerAngle**: Steering angle sensor
  - `getAngle()`: Get steering wheel angle
  
- **Snsr_WheelSpeed**: Wheel speed sensors
  - `getSpeed()`: Read individual wheel speeds

#### 5. ADAS Device Domain
**Sensors**:
- **Snsr_Camera**: Camera sensor
  - `ntfRawData()`: Provide raw image data
  - `ntfEncodeData()`: Provide encoded video stream
  
- **Snsr_Radar**: Radar sensor
  - `getSonarData()`: Provide radar reflection data
  
- **Snsr_Lidar**: Lidar sensor
  - `getPointCloud()`: Provide point cloud data
  
- **Snsr_Ultrasonic**: Ultrasonic sensor
  - `getDistance()`: Measure proximity distance
  
- **Snsr_IMU**: Inertial Measurement Unit
  - `getAcceleration()`: Read acceleration data
  - `getGyroscope()`: Read angular velocity
  
- **Snsr_GPS**: GPS receiver
  - `getPosition()`: Get latitude/longitude
  - `getAltitude()`: Get elevation
  - `getTime()`: Get GPS time

---

## Architecture and Implementation

### 4-Layer Software Architecture

1. **Application Layer**
   - User applications and vehicle-specific features
   - Third-party apps and services
   
2. **Atomic Service Layer (Part 1)**
   - Standardized functional services
   - Hardware-independent interfaces
   - Business logic implementation
   
3. **Device Abstraction Layer (Part 2)**
   - Hardware abstraction interfaces
   - Vendor-independent device control
   - Direct hardware interaction
   
4. **Foundation Platform Layer**
   - Operating system (Linux, QNX, etc.)
   - Basic computing resources
   - Hardware drivers

### API Call Flow Example: "Open Window"

1. **User Input**: Touch "Open Window" button
2. **Application Layer**: Handle UI event
3. **Atomic Service Call**: `BCM_Window.open()`
4. **Service Logic**: Determine required hardware actions
5. **Device Abstraction Call**: `Actr_DoubleHallMot.setOper(dir=UPWARD, dutyRat=100)`
6. **Hardware Action**: Motor rotates to open window
7. **Feedback**: `Actr_DoubleHallMot.ntfHallQuarterCnt()` reports position

### Key Benefits

#### For Developers
- Simplified API without hardware complexity
- Consistent interfaces across different vendors
- Rapid application development
- Code reusability

#### For OEMs
- Hardware vendor flexibility
- Reduced development costs
- Faster time to market
- Ecosystem expansion

#### For Suppliers
- Clear interface specifications
- Competitive differentiation through implementation
- Broader market access
- Innovation opportunities

### Version 4 Enhancements

#### New APIs Added
- Extended TMS APIs (4.9.24-4.9.29)
- Enhanced ADAS perception capabilities
- Improved energy management functions
- Additional HMI interaction methods

#### Performance Improvements
- Reduced latency in critical functions
- Optimized data structures
- Enhanced error handling
- Better resource management

### Participating Organizations

#### Lead Organization
- China Association of Automobile Manufacturers (CAAM) Software Division

#### Major OEMs
- BYD, GWM (Great Wall Motors), Geely, FAW, SAIC
- Changan, GAC, Dongfeng

#### Tier-1 Suppliers & Technology Companies
- Huawei, Bosch, Continental, Baidu
- Tencent, Alibaba, ZTE, Xiaomi

### Strategic Implications

#### Industry Impact
- Unified development standard for Chinese market
- Reduced fragmentation in automotive software
- Accelerated innovation cycles
- Lower barriers to entry for software developers

#### Global Competition
- Challenge to existing standards (AUTOSAR, GENIVI)
- Potential for international adoption
- Influence on global SDV development
- New competitive dynamics in automotive software

### Future Outlook

#### Planned Developments
- Integration with cloud services
- Enhanced V2X communication APIs
- AI/ML service integration
- Expanded cybersecurity features

#### Market Evolution
- Transition to service-oriented business models
- Emergence of automotive app stores
- Continuous feature updates via OTA
- Data-driven value creation

---

## Recommendations for International Markets

### For Global OEMs
1. Evaluate compatibility with existing architectures
2. Consider dual-strategy approach for Chinese market
3. Assess intellectual property implications
4. Plan for ecosystem participation

### For Technology Suppliers
1. Develop compatible solutions
2. Establish partnerships with Chinese companies
3. Invest in local R&D capabilities
4. Adapt products for standard compliance

### For Regulatory Bodies
1. Monitor standard evolution and adoption
2. Assess cybersecurity and safety implications
3. Consider harmonization opportunities
4. Develop appropriate regulatory frameworks

---

*This document provides a comprehensive summary of the Chinese SDV Standard Version 4 Beta 1. For detailed technical specifications, please refer to the original standard documents.*