### Journal
#### Time spent in CAD: 60 Hours
#### Estimated time spent in total (including research, journaling, shopping): ~100+
Historically, hackclub hardware projects are notorious for not being completed or built after submission and purchase of parts. The ones that are,
often end up forgotten, abandoned, or scrapped. 
I too am guilty of this, with my previous machines being salvaged for future projects in order to
save costs and budget, and because the past projects have either reached the end of their service/utility lives or serve no practical use in the future.

With outpost's extended budget, I wanted to try something new. A project that is useful, a project that lasts, and a project that can continue to be a project for many years into the future. A no-compromises, all out project that represents the absolute limit of my creativity and skill.

I decided, with the current toolchanger arms race kicked off by bondtech's INDX, snapmaker's U1 system, and bambulab's Vortek, I wanted to prove that open-source, democratized printers don't need to live in the past, and that I would create something that is both affordable, and functional.

To lay it out, this machine
is built around the same spirit as the CORE ONE L INDX, bambulab H2C, PRUSA XL, and ZeroG mercury one. I decided i would build the machine around a modified skeleton of an old Ender 5 plus, a very popular and affordable legacy large format fdm printer. I also set the design targets (specs) as so:

377x377x400MM build volume

Corexy, Closed loop servo system

9MM belt system gantry with liveshafts and double shear

High Temperature Carbon fiber X-axis tube

1KW mains bed

800W chamber heating system with intelligent power-sharing with the bed and hotends to allow dynamically set power limits

Muffled CPAP cooling system

Chamber ventilation

Structural steel panels

This project was created from a culmination of short logins and a variation of extended, and brief efforts, Some simple parts may take near months, 
and some complex parts have been done in a matter of minutes due to fluctuations in concentration and work enviroment.
There is no hour-to-dollar ratio, 
so it's not like there's any point in frauding hours anyhow. 

<img width="1318" height="752" alt="image" src="https://github.com/user-attachments/assets/733f8ba0-487a-4d51-88ff-0e059a437c9e" />
please dont overfeed your 3d printer.
## Part 1: The body (5/9/26-5/15/26)
<img width="988" height="1099" alt="image" src="https://github.com/user-attachments/assets/82b6e08e-a01f-4408-82a0-7eea392606cb" />

To begin, this printer is based off an ender 5 plus frame. the extrusions on top were replaced and rotated, along with the front extrusion. 
3MM hot roll steel structural panels were added to increase rigidty, sound insulation, and thermal counterbalancing for the linear rails. 
Extrusions were added on the bottom to serve as mounting points for DIN components, and other components that may need rigid mounting. 
An ACM skidplate was added because of it's durability, affordability, and fire retardance in the event of any mishaps, and to protect  it 
better than plywood or plastic in the event the bottom encounters any damage or impact. Blue spacers with completely locking casters were added to raise the machine, 
and make it easier to transport a heavy machine like this one, without letting it roll away. Handles were added to enable the lifting of the machine (into trucks, or onto tables)
Large vents were added to allow the electronics to breathe, they are flat on one side to enable the cooling of electronics. While they might not have cool geometric patterns like voron vents,
I think they look okay and reinforce the "Form over function" soul of this machine. 
## Part 1.1: Door (5/19/26)
<img width="976" height="1044" alt="image" src="https://github.com/user-attachments/assets/fac31f15-c918-4ec4-af56-e561adb9289a" />
I added a nice robust, and sealed door made with 1515 extrusions as the frame, and handle that pushes the flange seal to trap heat. 

## Part 2: Z-axis (5/19/26-5/25/26)
<img width="803" height="829" alt="Image" src="https://github.com/user-attachments/assets/12f82d21-7cbe-49cb-8c90-e882d33d8822" />
The Z axis is pretty simple. It reuses a large amount of components from the original ender 5 z axis, however it's been modified to fit the new frame, and has a 1kw heating pad to improve heating times, a thermal fuse mounted for safety in the event of an SSR failing (which oftentimes happens in the closed state), and an edge thermistor to compare temperature deltas to monitor the heatsoaking process. Unfortunately, the bed remains the stock steel sheet, as graphite or a cast bed would cost an astronomical amount and the extreme warpage can be compensated with the high-resolution eddy current scanner in this machine. 

## Part 3: CoreXY gantry (5/25/26-6/10/26)
<img width="1358" height="822" alt="Image" src="https://github.com/user-attachments/assets/5b2449ef-d9a3-4a06-82e1-f583193ea62a" />
The corexy gantry was one of the more difficult parts of the design. While based on the monolith gantry, the XY joints, and motor mounts had to be completely redesigned in order to support the new motion system and fit the needs of this machine. The XY joints have modified bump stops to change the endstop position to avoid toolhead collision with Z-axis components, and the motor mounts are redesigned to support a new, relatively unexplored method of control in 3dp. Because this remains relatively uncharted territory, I developed semi-custom servos for this application. I started off with the falcon 500 motor body, as it's incredibly powerful (6000rpm, 4.7nm) at only 12 volts. with an increased voltage, at 24, or even 48 these motors have great response and torque. The controller will be an odrive an an mt6835, and the servo is given a 3:1 reduction before driving the main drive pulley. because of the encoder's 2.1 million positions, this gives the main pulley 6.3 million positions per rotation, or a theoretical (not practical!) gantry resolution of 6.5nm, which is comparable to modern photolithography nodes for cpu/gpu manufacturing. While this number obviously isnt being used, it provides an incredibly high-resolution, low noise value for the PID loop to use, giving it incredible smoothness and response (The shaft will feel as if it's welded in place), benefiting total stiffness within the system (Steppers act like springs in their gantries due to laws of magnetism) and quality. The reduction is tensioned by a sliding, and locking plate that moves the motor. The gantry features double shear, and liveshaft idlers because of the extreme belt tensions required by the 9mm GT2 EPDM belting, which is thicker than standard and is required to handle the extra loads. The X axis is also constructed from a high temperature resistant carbon fiber box tube, which has superior stiffness, while weighing a fraction of the extrusion. The gantry uses a MGN12H rail for X, and MGN9H for Y to provide high strength and reduce wear on the gantry, and a supporting extrusion has been aded to the motor mounting system to improve rigidity and strength. 

## Part 4: Toolhead (6/11/26-6/20/26)
<img width="750" height="984" alt="Image" src="https://github.com/user-attachments/assets/1e6b0499-5f89-40a5-aa57-e10c8acaa47d" />
The toolhead was another fun part to deal with. While it appears to simply be an XOl toolhead on the outside, a deeper dive shows that it's nearly unrecognizable from a design standpoint. The ducts, body, and frame of the toolhead have been completely redone to support the hotend, a lancer meltzone long WITH a meltzone extender to support increased flowrates. The ducts are configured to support a CPAP cooling setup, which at this level is the bare minimum to cool the freshly extruded plastic. I also added extra mounting points to the updated carriage, which I then put a plate and mounting system for external mini tools. These tools dont quite have the cooling or extrusion power of the main, ultra-long cpap cooled hotend, but are still built with bambu X1C/P1S hotends, giving them solid performance at a very cost-efficient package. These hotends are continiously connected both electronically and filament wise, making them independently controlled, in a future update, a shared MMU system to distribute filament between all the hotends is in the works, however the tools will be passively cooled when docked and are bowden driven by an externally placed BMG clone extruder, requiring them too cool and re-heat, however a future dock update will also bring cooling to all tools at all times, allowing them to maintain printing temperature and limit the toolchange speed to the actual speed of the gantry (which of course is pretty darn high!). While on the toolhead, the tools are actively cooled by a 3010 radial fan. 
<img width="354" height="597" alt="Image" src="https://github.com/user-attachments/assets/3e863a22-134c-45f8-be95-ada59a46a835" />
The tools use a multipoint, magnetically assisted locking system that uses pins and bearings to handle the initial contact and allignment, but rely on the ball-end nuts and neodymium magnets to provide consistent allignment. The pin and slider mechanism on the bottom left locks the tool in place in the event of a crash, or other mishap this mechanism prevents the tool from totally detaching, allowing the tool to continously stay in the margin required for the self-allignment mechanism to work, though the locking mechanism itself does not provide any allignment. This method of toolchanging is incredibly fast, and reliable but comes at the cost of size efficiency. in it's current config, even this massive machine only has room for 4 tools total (Main + 3 extra tools), however similar to bambulab's vortek, I also plan to add a "droprack" that leverages the extra vertical space to increase the tool count to 7.

## Part 5: The Chamber
<img width="458" height="587" alt="Image" src="https://github.com/user-attachments/assets/69313c9c-7086-4c15-bb82-15286ba823f1" />
In order to be able to hit the specified targets of this machine, and retain function accross a wide range of operating conditions, the printer must be able to both handle a wide variety of materials. It cannot just be insulated heavily as that can sacrifice performance for lower temperature materials, like TPU, PLA, and PETG, however it cannot be open air for materials like PPS, PA, PC, ABS, ASA, or even PEKK. Instead, I created a hybrid system that incorporates both ventilation, and active chamber heating. I added a hinged "Greenhouse" Tophat, constructed from thick, 1/4 inch polycarbonate, printed brackets, and extrusions. At the top, are 2 server grade 120MM fans to move massive amounts of air when printing lower temperature materials. These fans will be disabled and covered for higher temperature operation, which uses the two chamber heaters at the bottom. The chamber heater holders will be printed out of PA6-GF, which as a HDT of 190C (far beyond the max temp of the ptc, which is 110 during operation and has an emergency cutoff that stops it at 120c, along with a fuse to blow if both systems fail), meaning that the chamber heater will never exceed that temperature thanks to the PTC element's nature. The two heaters are placed at the edges of the bottom and blown by massive, 12032 blowers that push huge amounts of air through the heaters. The airflow is designed to follow the natural convection pattern of the chamber, increasing efficiency and eliminating hot/cold spots. The chamber has also been lined with 3/4in polyiso foam, to effectively trap heat to allow higher temperatures and better energy efficency. when printing lower temperature materials, the chamber heater fans will be activated but not the PTC units themselves, circulating cold air in the chamber and providing a minor sheet cooling effect to the print plate. A future update is planned to add a massive array of 12032 blowers to function as additional sheet cooling. 
<img width="194" height="594" alt="Image" src="https://github.com/user-attachments/assets/6c465200-1d86-4211-bbe5-b06e6bfc67e6" />
Additionally, a large purge bin with a removable bucket at the bottom has been added to allow for automatic purging with future MMU systems and tool priming. 
