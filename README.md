# Gabe’s BeamNG Transmission Pack
## Introduction
Gabe's transmission pack is a (soon to be) huge collection of transmissions available for some vehicles in BeamNG. Support expands with each update and the end goal is to have support for all official vehicles, with some modded vehicle support. 
Hundreds of hours have gone into the development of this project and it's just me (Gabe) working on it, so updates are somewhat few and far between. 

## Changelog
You can view the changelog by clicking on the changelog file in the root directory of this repo. 

## Supported Vehicles
There are two types of support for this pack, full support and partial support. Full support means that all transmissions that are available in the pack will work on that vehicle. Partial support means that at least one of the available transmissions works on that vehicle.
### Full Support
- ETK 800
- ETK 1300 (Modded)
- Bruckell Bastion
### Partial Support
- Civetta Scintilla
- ETK I-Series
- Hirochi SBR
- Autobello Piccolina

## Mod Support
Mod support is in its very very early stages, and my pack currently only supports one mod: ETK 1300.
All transmissions that are available for the ETK 800 are available for the ETK 1300, entirely unchanged. 

## Transmissions
### GDC
GDC Transmissions are one of the two main focuses of the project. The main focus of the GDC was to have a transmission that was customizeable, entertaining, and free from lack of character. To do this, I gave it the best shift logic that I have made, which keeps improving with every update, as well as the best of my technologies.

### Hypershift
Hypershift transmissions are highly advanced iterations of torque-converter automatic transmissions, and are the second main focus of the project. You can read more about the specifics of hypershift technology down in the technology section. The goal was to take the downfalls of a traditional automatic transmission and overcome them, at minimal cost to driving experience and smoothness. 
### CVT
The goal of CVT transmissions is usually to get the best fuel efficiency possible, but my CVTs are tuned for throttle response and peak power on demand. Fuel efficiency is good too, due to the nature of CVT transmissions, but that wasn't the main focus. My CVTs are capable of handling huge amounts of torque, so they're ideal for towing heavy loads up hills, or you can pair them with a big V8 to get some insane quarter mile times.

### Automatic
These transmissions only exist in the pack as a testament to how it all started. The first public release of the pack came approximately two years after I started developing transmissions for BeamNG, since I originally had no plans (or means) to share them with the public. The first couple of transmissions in the pack that I made were automatic transmissions. Then came the CVTs and so on. If you want a history lesson, keep reading and you can learn about the origin story of the pack. Some of the automatic transmissions aren't bad, such as the 10-speed, 12-speed and 6-speed, but the others are not quite as reliable or fun to drive. It's usually a safe bet to just stick to the other types of transmission unless you're looking for that slow but smooth torque-converter shift. 
### Manual
Manual transmissions are key to the driving experience for many people, so I didn't want to let you guys down by not having any. As far as I'm aware, there are no 7-speed manuals included anywhere without a mod in BeamNG, so I had to do something about that. I didn't bother making a 6-speed since almost every car in BeamNG has a 6-speed, and if it doesn't, it has either a 5-speed or 4-speed manual. I haven't ruled out making different manual transmissions in the future, but for now, this is what we got. 

## Origin Story
Gabe’s transmission pack started as just me tinkering with values in the `vehicleController` of my ETK 800, to try and make it up shift faster when I got off the throttle. As mentioned above, I started with the traditional automatic transmission.

Once I was content with my handicraft, I decided to try and make a 7speed manual transmission which was ideal for cruising on the highway at 120km/h. 

After some time, I decided to make a CVT so my engine would stay at peak power the whole time I was accelerating. I made CVTs for different engine types, even some ridiculous modded engines that revved to 11,000RPM. 

Once I had finished with the CVT bandwagon, I wanted to make something completely new. I wanted to make a transmission that worked like an automatic, but had shift speeds and smoothness that would rival a DCT, and so the hypershift technology was born. After about 100 iterations, it evolved to what It is today. 

After working on the hypershift transmissions for so long, I wanted to switch it up, so I tried to make a DCT transmission that was better than my hypershift transmissions. As mentioned above, customizability and driving experience were the name of the game, so that’s what I focused on, developing technologies and making tweaks along the way. 

## Technologies
### Hypershift Technology
Gabe's Hypershift Technology works by decreasing the weight (and therefore inertia) of a standard automatic transmission to increase shift speed, modifying the rev-match throttle mapping to create snappier downshifts, and also using Gabe's Shift Logic to produce the smoothest and most responsive driving experience.
> Note: Hypershift Transmissions use Gabe's Balanced Shift Logic

Hypershift transmissions are recommended where GDC transmissions are unavailable instead of traditional automatic transmissions.
Traditional Automatic Transmissions, such as "Gabe's 10-Speed Automatic Transmission" do not use the most up-to-date version of Gabe's Shift Logic since they are not actively being developed. 

### Gabe's Shift Logic
There are three types of shift logic:
#### Balanced
- Designed to best mimic the behaviour of a real dual-clutch transmission's shift logic, with some of my personal enhancements.
- GDC Transmissions use Gabe's Clutch Launch Technology to improve off-the-line acceleration and give more control when reversing. 
- Has nearly instantaneous downshift response for passing on the freeway, but will also keep the RPM low while cruising for higher efficiency.
- Will not hesitate to downshift to redline on full throttle.
 
#### Maximum Performance (Track Mode)
- Designed for maximum acceleration and maximum throttle response.
- Holds RPMs high and downshifts early.
- GDC Clutch Launch will rev the engine approx 2x as high as balanced mode to give up to a 50% faster launch. 
- Regular "D" mode is not available. Only sport and manual shifting options are permitted.
#### Maximum Fuel Efficiency
- Designed for maximum fuel efficiency.
- Upshifts early to keep the engine rpm as low as possible for the best combustion efficiency percentage. 
- Greatly dulls throttle response, and doesn't downshift very often
- When downshifts do occur, it will typically not downshift above 4000RPM.
- In an emergency situation where full throttle is applied, the transmission will let the engine rev out until peak power, but will not downshift as stated above.
- Sport mode and manual mode are not available.

### Gabe's Clutch Launch Technology
#### Parameters
```
"clutchLaunchTargetRPM"
"clutchLaunchStartRPM"
```
The values for these parameters are a "trade secret" (jk), but I won't publish them here to avoid people copying my work. 
The goal of the clutch launch is to produce, well, a faster launch. 


Here's how it works:

##### Step 1
Rev the engine to a specific RPM with the clutch disconnected.
This RPM will be a multiple of "clutchLaunchTargetRPM" based on the throttle percentage. 
"cluchLaunchStartRPM" determines the lowest RPM allowed during the clutch launch. In balanced and maximum fuel efficiency mode, this value is very low so that smooth, low-rpm starts are possible. In track mode (maximum performance), the clutch launch rpm will always be very high.
> The full-throttle "clutchLaunchTargetRPM" is determined by the shift logic mode selected. Maximum Fuel Efficiency mode does not use this technology in the same way that Balanced and Maximum Performance modes do (won't rev past 1500rpm when getting off the line).
##### Step 2
The computer uses the wet clutch to bring the transmission (in first gear) up to the speed of the engine as fast as possible.

##### Step 3
Once the engine and transmission are matched, the clutch launch is finished, so we drop the clutch all the way and let the transmission shift gears normally according to the shift logic mode that's selected. 

### Gabe's SelectShift Technology
- Allows the user to select the gear ratios that the transmission uses in the part selector! (Only available on GDC Transmissions)
- Each gear ratio comes with a recommended final drive ratio to use.   
#### Ratio Options
- Gabe's Gearing
- ZF 8HP
- 9-Speed AMG-GTronic
- 7-Speed PDK

