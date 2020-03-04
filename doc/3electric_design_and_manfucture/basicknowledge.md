
## Basic PCB Concepts

1. Defination
	A **printed circuit board** or **PCB**, is a plate or board used for placing the different elements that conform an electrical circuit that contains the electrical interconnections between them.
	The most simple printed circuit boards are the ones that contains copper tracks or interconnects only on one of its surfaces. These kinds of boards are known as 1 layer printed circuit board or 1 layer PCB.
	The most common PCB's manufactured today are the ones that contain 2 layers, that is, you can find interconnects in both surfaces of the board. However, depending on the physical complexity of the design ( PCB layout ), the boards can be manufactured of 8 or more layers.
	![PCB 2 layer example](https://resources.nexpcb.com/hs-fs/hubfs/Imported_Blog_Media/pcb-2-layer-printed-circuit-board-concepts-1.jpg?t=1517371339312&amp;width=500&amp;height=230&amp;name=pcb-2-layer-printed-circuit-board-concepts-1.jpg)
	![](https://ws4.sinaimg.cn/large/006tNc79gy1foo1x2xi24j30xc0p0412.jpg)
	** Example region of a 2 layer PCB**

2. Basic structure 

3. Applycation 




## Terminology description 

#### layers
The printed circuit boards can be made of several layers. When a PCB is designed with the aid of an EDA software, often are specified several layers that doesn't necessary correspond to conductive material ( copper ). For example, the silkscreen and soldermask are nonconductive layers. Having conductive and nonconductive layers may lead to confusion, because manufacturers use the term layer when they are referring to the conductive layers only. From now on, we are going to use the term layer without the suffix "CAD" only when referring to conductive layers. If we use the term "CAD Layer" we are referring to all kinds of layer, that is, conductive and nonconductive.

The CAD Layer stackup is the following:

|CAD Layer (conductive and nonconductive)|CAD Layer description|
| ----- | ----- | 
| 1 |  Top silkscreen/overlay ( nonconductive ) |  
| 2 |  Top soldermask ( nonconductive ) |  
| 3 |  Top paste mask ( nonconductive ) |  
| 4 |  Layer 1 ( conductive ) |  
| 5 |  Sustrate ( nonconductive ) |  
| 6 |  Layer 2 ( conductive ) |  
| ... |  ... |  
| n-1 |  Sustrate ( nonconductive ) |  
| n |  Layer n ( conductive ) |  
| n+1 |  Bottom paste mask ( nonconductive ) |  
| n+2 |  Bottom solder mask ( nonconductive ) |  
| n+3 |  Bottom silkscreen/overlay ( nonconductive ) | 


The following picture shows 3 different stackups. The orange color highlights the layers in each stackup. The stackup height, or board thickness can vary depending on the application, however the most used is 1.6 [mm] or 62 [mils]. In some countries [thou] is used as a synonym for [mils]. ( `1 [mil] = 0.001 [inch] = 0.0254 [mm]` )
![stackup - printed circuit board concepts PCB](https://resources.nexpcb.com/hs-fs/hubfs/Imported_Blog_Media/stackup-printed-circuit-board-concepts-1.jpg?t=1517371339312&amp;width=300&amp;height=180&amp;name=stackup-printed-circuit-board-concepts-1.jpg)

** Example of 3 different PCB stackups: 2 layers (a), 4 layers (b) and 6 layers (c)**


#### solder mask, silk screen
1. Soldermask
	For mounting the electrical components on the printed circuit boards, an assembly process is required. This process can be done by hand or through specialized machinery. The assembly process requires the use of solder to place the components on the board. For avoiding or to prevent the solder to accidentally short-circuit two tracks from different nets, pcb manufacturers apply a finish or varnish called soldermask on both surfaces of the board. The most common color of soldermask used in printed circuit boards is green, followed by red and blue.
	In EDA software (Electronic design automation), generally exist a rule associated to the expansion of the soldermask. This rule specifies the distance that exists between the pads' borders and the soldermask's border. This concept is illustrated in figure 2 (a).

2. Silkscreen or Overlay
	Silk-screening is the process where the manufacturer prints information on the soldermask conducive to facilitate the processes of assembly, verification and repair. Generally the silkscreen is printed for indicating test points as well the position, orientation and reference of the electronic components that are part of the circuit. Also it can be used for any purpose that the designer may require, for example, the company name, configuration instructions (this was commonly used in old PC motherboards), etc. The silkscreen can be printed on both surfaces of the board. Also the term silkscreen is known as overlay. The following picture shows a region of a circuit, all the printings made in white correspond to the silkscreen.

![soldermask and silkscreen ](https://resources.nexpcb.com/hs-fs/hubfs/Imported_Blog_Media/soldermask-silkscreen-printed-circuit-board-concepts-1.jpg?t=1517371339312&amp;width=500&amp;height=285&amp;name=soldermask-silkscreen-printed-circuit-board-concepts-1.jpg)

** Soldermask expansion (a) and silkscreen (b)**


#### Pad
A pad is a small surface of copper in a printed circuit board that allows soldering the component to the board. You can think of a pad as a piece of copper where the pins of the component are mechanically supported and soldered. There are 2 types of pads; thru-hole and smd (surface mount).

Thru-hole pads are intended for introducing the pins of the components, so they can be soldered from the opposite side from which the component was inserted. These types of pads are very similar to a thru-hole via.

The smd pads are intended for surface mount devices, or in other words, for soldering the component on the same surface where it was placed.

The following picture depicts 4 components. The components IC1 and R1 have 8 and 2 SMD pads respectively, while both components Q1 and PW have 3 thru-hole pads.

![pads - printed circuit board concepts PCB](https://resources.nexpcb.com/hs-fs/hubfs/Imported_Blog_Media/pads-printed-circuit-board-concepts-1.jpg?t=1517371339312&amp;width=500&amp;height=163&amp;name=pads-printed-circuit-board-concepts-1.jpg)

** SMD and Thru-hole Pads**


#### vias
1.  Plated Holes (Thru-hole Vias or Full Stack Vias)
	When an interconnect must be made from a component that is located on the top layer of the printed circuit board with another that is located at the bottom layer, a via (Vertical Interconnect Access) is used. A via is a plated hole that allows the current to pass through the board. The following picture depicts 2 tracks that begin at the pads of a component on the top layer and end at the pads of another component at the bottom layer. For conducting the current from the top layer to the bottom layer, a via is used for each track. The tracks and pads that belong to the bottom layer are visually dimmed, so you can differentiate them from the ones that are on the top layer.
	![vias - printed circuit board concepts PCB](https://resources.nexpcb.com/hs-fs/hubfs/Imported_Blog_Media/vias-printed-circuit-board-concepts-1.jpg?t=1517371339312&amp;width=500&amp;height=240&amp;name=vias-printed-circuit-board-concepts-1.jpg)
	**Two integrated circuits located on opposite sides of the PCB are connected using thru-hole vias**
	It depicts a more detailed view of a transversal section of a 4 layer printed circuit board or 4 layer PCB. The colors that appear in the Figure are explained in the following table:

	| Color  | Legend| 
	| -----  | ----- |    
	| green  | Top and bottom soldermasks   |  
	| red    | Top layer ( conductive )     |  
	| violet | Second layeris used as a power plane ( i.e. Vcc or Gnd ) |  
	| yellow | Third layer is used as a power plane ( i.e. Vcc or Gnd) |  
	| blue   | Bottom Layer ( conductive )      | 

	The PCB depicted above shows a track that belongs to the top layer that goes through the board using a thru-hole via, and then continues as a track that belongs to the bottom layer.
	![thru-hole via - printed circuit board concepts PCB](https://resources.nexpcb.com/hs-fs/hubfs/Imported_Blog_Media/via-thruhole-PCB-4-layers-printed-circuit-board-concepts-1.jpg?t=1517371339312&amp;width=500&amp;height=327&amp;name=via-thruhole-PCB-4-layers-printed-circuit-board-concepts-1.jpg)

	**Track from the top layer going through the PCB and ending on the bottom layer**

2. Blind vias
	In high density complex designs is necessary to use more than 2 layer. Generally in multilayer system designs where there are many integrated circuits, power planes ( Vcc or gnd) are used to avoid excessive routing for power rails. In other words, it is lot easier and more secure to directly connect to the power planes that are beneath the chips instead of routing long tracks for the PDS ( Power Delivery System ) ( this can also be achieved with thru-hole vias ). Also there are times that a signal track must be routed from an external layer ( top or bottom ) to an internal layer with minimum via height because it can act as a stub and maybe produce an impedance mismatch. This can cause reflections and produce signal integrity issues ( more on this in a future article ). For these kinds of interconnects blind vias are used, which allows a connection to be made from an external layer to an internal layer with minimum via height. A blind via starts on an external layer and ends on an internal layer, that's why it has the prefix "blind".
	To know if a certain via is blind, you can put the PCB against a source of light and see if you can see the light coming from the source through the via. If you can see the light, then the via is thru-hole, otherwise the via is blind.
	It is very useful to use these kinds of vias in printed circuit board design when you don't have too much space for placing components and routing. You can put components on both sides and maximize the space. If the vias were thru-hole instead of blind, there would be some extra space used by the vias on both sides.
	The following picture depicts 3 vias that are part of 4 layer printed circuit board. If we see the picture from left to right, the first via that we will see is thru-hole via or fullstack via. The second via begins at the top layer and ends at the second layer ( inner ), so we say that this is a 1-2 blind via. At last, the third via begins at the bottom layer and ends at the third layer, so we say that this is a 3-4 blind via.
	It is important to have in mind that blind vias are often manufactured in consecutive layers, in other words between L1 L2, L3 L4, Ln-1 Ln.
	![blind via - printed circuit board concepts PCB](https://resources.nexpcb.com/hs-fs/hubfs/Imported_Blog_Media/blind-via-printed-circuit-board-concepts-1.jpg?t=1517371339312&amp;width=500&amp;height=255&amp;name=blind-via-printed-circuit-board-concepts-1.jpg)

	** Comparison between a Thru-hole and a Blind via**
	The disadvantage of this type of via is its high price when compared to the thru-hole alternative.

3. Buried Vias
	These vias are similar to the blind ones, with the difference that they begin and end on an inner layer. If we look at the image depicted in the floowing picture from left to right, we see that the first one is a thru-hole or full stack via. The second one is a 1-2 blind via, and the last one is a 2-3 buried via that begins on the second layer and ends on the third layer.
	![burried via - printed circuit board concepts PCB](https://resources.nexpcb.com/hs-fs/hubfs/Imported_Blog_Media/burried-via-printed-circuit-board-concepts-1.jpg?t=1517371339312&amp;width=500&amp;height=279&amp;name=burried-via-printed-circuit-board-concepts-1.jpg)
	** Comparison between Thru-hole vias, Blind vias and Buried vias**
	It is important to have in mind that blind vias are often manufactured in consecutive layers (i.e. L1 L2)
	As the case of blind vias, the main disadvantage of this type of via is its high price when compared to the thru-hole alternative. 









####Copper tracks
A track is conductive path that is used to connect 2 points in the PCB. For example, for connecting 2 pads or for connecting a pad and a via, or between vias. The tracks can have different widths depending on the currents that flow through them.
It is important to highlight that in high frequencies is necessary to calculate the tracks' width so that the interconnect can be impedance matched along the path created by the track. ( more on this in a future article )

![tracks - printed circuit board concepts PCB](https://resources.nexpcb.com/hs-fs/hubfs/Imported_Blog_Media/tracks-printed-circuit-board-concepts-1.jpg?t=1517371339312&amp;width=500&amp;height=242&amp;name=tracks-printed-circuit-board-concepts-1.jpg)
**Tracks that interconnect 2 integrated circuits (chips)**



***
## PCB fabrication
####Etching
1. Lithography
2. Transfer
3. Ferric/cupric chloride, ammonium/sodium persulfate
4. [SDS][1]
5. Waste disposal






## Design 
#### design rules
width/spacing (15, 5 mils)






####components
1. through-hole
2. surface-mount
3. chip-scale
4. breadboards


#### [Component packages](https://en.wikipedia.org/wiki/List_of_integrated_circuit_packaging_types)
Today in the market you can find a great variety of electronic component packages. It is common to find several types of packages for one device. For example you can find the same integrated circuit in [QFP's](https://en.wikipedia.org/wiki/Quad_Flat_Package) and [LCC's](https://en.wikipedia.org/wiki/Chip_carrier#Plastic_leaded_chip_carrier) packages.

Basically there exist 3 big families of electronic packages:

| Package |  Description |  Example Image | 
| ----- | ----- | ----- | 
| Thru-Hole | Are all those components that have pins intended to be mounted through a plated hole in the PCB. This kind of component is soldered to the opposite side of the board from which the component was inserted. Generally these components are mounted on one surface of the board only.|  ![thru-hole components - printed circuit board concepts PCB](https://resources.nexpcb.com/hs-fs/hubfs/Imported_Blog_Media/thruhole-printed-circuit-board-concepts-1.jpg?t=1517371339312&amp;width=100&amp;height=100&amp;name=thruhole-printed-circuit-board-concepts-1.jpg) |  
| SMD/SMT (surface mount device/surface mount technology)| Are all those components that are soldered in the same side of the board from which the component was placed. The advantage of this type of package is that it can be mounted on both sides of the PCB. Also, these components are smaller than the thru-hole type, which allows the design of smaller and denser printed circuit boards. These types of components are useful for frequencies up to 200 [MHz] (fundamental clock frequency).|  ![smd components - printed circuit board concepts PCB](https://resources.nexpcb.com/hs-fs/hubfs/Imported_Blog_Media/smd-printed-circuit-board-concepts-1.jpg?t=1517371339312&amp;width=100&amp;height=100&amp;name=smd-printed-circuit-board-concepts-1.jpg)|
| BGA (Ball grid array) | These types of components are frequently used for high density pin integrated circuits. For soldering them to the printed circuit boards it is required to have specialized machinery due that the pins are made of solder balls that have to be melted for making the electrical contact with the pads.BGA components are ideal for high frequency integrated circuits due to the very small parasitic inductances present in the joint between the pad and the balls. These type of components are very common in computer hardware like motherboards and video accelerator cards.|  ![bga components -  printed circuit board concepts PCB](https://resources.nexpcb.com/hs-fs/hubfs/Imported_Blog_Media/bga-printed-circuit-board-concepts-1.jpg?t=1517371339312&amp;width=100&amp;height=100&amp;name=bga-printed-circuit-board-concepts-1.jpg) | 


For more information,reference wikipedia.[Surface Mount Technology - Wikipedia](http://en.wikipedia.org/wiki/Surface-mount_technology "Tecnología de Montaje Superficial - Wikipedia")




####Design software
1. eagle

***
## Material
#### rigid
1. FR4 (epoxy glass)
2. [FR1][13] (phenolic paper)

#### flex
1. [Kapton][14]
2. [#1 epoxy film][15]
3. [#1126 copper tape][16]
#### high-frequency
1. teflon
2. glass

#### copper
1. 0.5 oz: 17.5 um
2. 1.0 oz: 35 um
3. 2.0 oz: 70 um





***
##[machining][2]
####[machines][3]
1. tools
             [0.010][4]
             [1/64][5]
             [1/32][6]
2. fixturing
3. underlay
4. orientation
5. zeroing
6. set-screws
7. lifetime
8. deburring
9. cleaning

#### [vinyl cutter][7] [flex][8]
####[laser cutter][9]
####[printing][10]
####[plating][11]
####[sewing][12]









***
##assembly
####[solder][32]
1. eutectic
2. wetting
3. flux
4. wire, paste, bar
5. manual, reflow, wave
6. [ROHS][33]

#### stuffing
1. component orientation
2. tacking down parts
3. bottom to top, inside to outside
4. fumes
5. washing

#### desoldering
1. [braid][34]
2. [hot air][35]
3. gravity

#### cutting traces, adding jumpers
#### [pick-and-place][36]
#### encapsulation



***
## CAM
#### formats
1. [Gerber/RS-274X][37]
2. [png][38] resolution
#### [mods][39]
1. [video][40]
#### trace width
1. [traces][41] 
2. [interior][42]
3. [1/64"][43]
4. [0.010"][44]






***
## Programming

***
## Debuging


***
## Effect



***



## board houses
#### vendor
1. [PCB:NG][17]
2. [AP Circuits][18]
3. [Advanced][19]
4. [Sierra][20]
5. [Screaming Circuits][21],
6. [AQS][22]
7. [Gold Phoenix][23]
8. [3PCB][24]
9. [Think &amp; Tinker][25]
10 .PCB, kit, BOM


***
## Update 


***
## Opinion

***
##QUESTION
1. LAYER 1 1.5,2,4,N   (What is 1.5layer)





the above is reference from 
1. [NexPCB](www.nexpcb.com)
2. [WIKI](https://en.wikipedia.org/wiki/Printed_circuit_board)

 

[1]: https://us.vwr.com/store/search/searchMSDS.jsp
[2]: http://www.youtube.com/watch?v=XdamEhs2RIk&amp;list=PL-xEsC0ZUCUM42QNHaOOdoOwYg0j251dU&amp;index=1
[3]: http://cba.mit.edu/tools
[4]: http://www.carbidedepot.com/00100in-DIA-220M-010-P70452.aspx
[5]: http://www.carbidedepot.com/00156in-DIA-2FL-SE-AlTiN-164-P180142.aspx
[6]: http://www.carbidedepot.com/00312in-DIA-2FL-SE-AlTiN-132-P180143.aspx
[7]: http://fab.cba.mit.edu/classes/863.17/Harvard/people/HonghaoDeng/project-3/project-3.html
[8]: http://fab.cba.mit.edu/classes/863.17/Harvard/people/HonghaoDeng/project-9/project-9.html
[9]: http://fabacademy.org/archives/2015/doc/fiber-laser-cutting-pcb.html
[10]: http://cba.mit.edu/events/13.03.scifab/index.html
[11]: https://www.google.com/search?q=electroplating
[12]: http://cba.mit.edu/docs/papers/00.07.E-broidery.pdf
[13]: http://www.globallaminates.com
[14]: http://www2.dupont.com/Kapton/en_US/
[15]: http://multimedia.3m.com/mws/media/37468O/3m-epoxy-film-electrical-tape-1.pdf
[16]: http://multimedia.3m.com/mws/media/104361O/tape-1126-copper-foil-with-conductive-adhesive.pdf
[17]: https://www.pcb.ng
[18]: http://www.apcircuits.com/
[19]: http://www.4pcb.com/
[20]: http://www.protoexpress.com/
[21]: http://www.screamingcircuits.com/
[22]: http://aqs-inc.com
[23]: http://www.goldphoenixpcb.biz/
[24]: http://www.3pcb.com
[25]: https://www.thinktink.com
[26]: http://academy.cba.mit.edu/output_devices/RGB/hello.RGB.45.jpg
[27]: http://academy.cba.mit.edu/output_devices/array/hello.array.44.jpg
[28]: http://academy.cba.mit.edu/output_devices/array/hello.array.44.2.jpg
[29]: http://fab.cba.mit.edu/classes/863.16/doc/tutorials/PCB_Rivets
[30]: http://octopart.com/
[31]: http://academy.cba.mit.edu/breadboard.jpg
[32]: https://www.digikey.com/products/en/soldering-desoldering-rework-products/solder/262
[33]: http://ec.europa.eu/environment/waste/rohs_eee/index_en.htm
[34]: http://www.digikey.com/product-detail/en/Q-B-10AS/EB1088-ND
[35]: http://www.amazon.com/Weller-6966C-Watts-Electric-Industrial/dp/B000ICGMN4
[36]: http://www.ddmnovastar.com/pick-and-place
[37]: https://www.ucamco.com/files/downloads/file/81/the_gerber_file_format_specification.pdf
[38]: http://academy.cba.mit.edu/embedded_programming/hello.ISP.44.res.traces.png
[39]: http://mods.cba.mit.edu
[40]: http://academy.cba.mit.edu/mods.mp4
[41]: http://academy.cba.mit.edu/linetest.png
[42]: http://academy.cba.mit.edu/linetest.interior.png
[43]: http://academy.cba.mit.edu/0156.jpg
[44]: http://academy.cba.mit.edu/010.jpg
[45]: http://fab.cba.mit.edu/classes/863.17/CBA/people/tomasero/index.html
[46]: https://jw4rd.github.io/shieldMill
[47]: http://fab.cba.mit.edu/classes/863.16/doc/projects/ftsmin/index.html
[48]: http://fabacademy.org/archives/2015/doc/projects/FabTinyStar/
[49]: http://fab.cba.mit.edu/classes/863.16/doc/tutorials/FabISP/FabISP_Demystified.html
[50]: http://fab.cba.mit.edu/classes/863.11/people/valentin.heun/2.htm
[51]: http://fab.cba.mit.edu/content/archive/projects/fabispkey/index.html
[52]: http://fab.cba.mit.edu/content/archive/projects/fabisp/
[53]: http://academy.cba.mit.edu/embedded_programming/hello.ISP.44.cad
[54]: http://academy.cba.mit.edu/embedded_programming/hello.ISP.44.png
[55]: http://academy.cba.mit.edu/embedded_programming/hello.ISP.44.components.png
[56]: http://academy.cba.mit.edu/embedded_programming/hello.ISP.44.traces.png
[57]: http://academy.cba.mit.edu/embedded_programming/hello.ISP.44.interior.png
[58]: http://academy.cba.mit.edu/embedded_programming/hello.ISP.44.res.cad
[59]: http://academy.cba.mit.edu/embedded_programming/hello.ISP.44.res.png
[60]: http://academy.cba.mit.edu/embedded_programming/hello.ISP.44.res.interior.png
[61]: http://fab.cba.mit.edu/about/fab/inv.html
[62]: http://search.digikey.com/scripts/DkSearch/dksus.dll?Detail&amp;name=ATTINY44A-SSU-ND
[63]: http://search.digikey.com/scripts/DkSearch/dksus.dll?Detail&amp;name=644-1039-1-ND
[64]: http://search.digikey.com/scripts/DkSearch/dksus.dll?Detail&amp;name=H2961CT-ND
[65]: http://www.mouser.com/ProductDetail/FCI/71600-006LF/?qs=yJYkLTYh5760qKJxwPD6hA%3d%3d
[66]: http://search.digikey.com/scripts/DkSearch/dksus.dll?Detail&amp;name=BZT52C3V3-FDICT-ND
[67]: http://search.digikey.com/scripts/DkSearch/dksus.dll?Detail&amp;name=311-0.0ERCT-ND
[68]: http://academy.cba.mit.edu/embedded_programming/firmware.zip
[69]: http://archive.fabacademy.org/archives/2016/doc/programming_FabISP.html

  
[70]:https://resources.nexpcb.com/blog/blogs/news/17683169-what-is-a-printed-circuit-board-basic-pcb-concepts