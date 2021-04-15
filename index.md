# Process Simulation of Methanol Production from Syngas
<p>
  <b>Author:</b> <a href="https://rajdeepdev10.github.io">Rajdeep Dev</a> <br>
  <b>UBC ID:</b> 71666887
</p>

<img src="./assets/images/cover-image.jpg" alt="chemical plant" width="400">

## Process Description

This project will focus on the production process of methanol from syngas. Syngas is a fuel mixture produced from natural gas that consists primarily of hydrogen, carbon monoxide, and carbon dioxide with small amounts of water, nitrogen, and methanol. On an industrial scale, methanol is predominantly produced from the reaction of hydrogen with carbon monoxide and carbon dioxide. The resulting gas mixture is then distilled to create pure methanol [[1]](/methanol-process-simulation/#references). This process is comprised of the following reactions is carried out at varying conditions [[2]](/methanol-process-simulation/#references): 

<div align="center">
  CO + 2H<sub>2</sub> → CH<sub>3</sub>OH (1) <br>
  CO<sub>2</sub> + 3H<sub>2</sub> → CO + H<sub>2</sub>O (2) <br>
  CO + H<sub>2</sub>O → CO<sub>2</sub> + H<sub>2</sub> (3)
</div>

Reaction 1 and 2 is carbon dioxide and carbon monoxide hydrogenation reaction to methanol. These reactions produce high amounts of crude methanol which is needed to purify by distillation. The operating condition is between 50-100 atm and 250 °C [[3]](/methanol-process-simulation/#references). Reaction 3 is known as “water-gas shift reaction” where carbon monoxide and steam are reacted using a catalyst to produce carbon dioxide and more hydrogen. The products from this reaction are recycled back to the hydrogenation reaction so it can work as reagents. Reaction 1 and 2 is endothermic reaction so low temperature and high pressure is favorable whereas water gas shift reaction is exothermic reaction. Catalysis will be ignored in this process simulation for each of the reactions. 

The simulation flowsheet begins with a stream carrying 150 kmol/h of syngas mixed with a recycle stream containing unreacted reactants. This mixture of reactants is sent to a REquil reactor (REACT) using the FEED stream. Since the reaction is operating at high temperature and pressure, reaction kinetics are much faster so a REquil reactor can be used to make a good model. The reactor operates at a temperature of 100 C and 20 atm to produce methanol, with water as side product. The vapor and liquid products from the reactor are mixed using MIX-102 and sent to the cooler (COOL) to cool the mixture to 10 C. This condenses most of the methanol while most of the unreacted gases remain in vapor phase. A flash 2 block (SEP) simply separates the condensate from the vapor stream. The vapor stream from the flash block is recycled back to the reactor, after removing 0.05 fraction of the gas as purge using a splitter (SPLIT). The liquid stream from the flash block (L-SEP) contains 0.96 mol fraction of methanol and is sent to a Distillation column (COLUMN) where 37.3 kmol/h of 0.999997 mol fraction methanol is recovered as bottom product from the distillation column. The process yield of methanol calculated per mole syngas feed is 24.9%, which is realistic compared to typical industrial yield of 25% [[4]](/methanol-process-simulation/#references).  


## Process Flowsheet

<img src="./assets/images/process-flowsheet.PNG"><br>
*Figure 1: Aspen Plus Flowsheet for Methanol Production*

## Operating Conditions

### Feed Streams

| Stream name  | Component(s)| Composition/ Flowrates|P/T/vap. frac.           |
|:----------------------:|:-------------:|:-------------:|:-------------------:|
| SYNGAS      | Hydrogen | 0.5 mole fraction (of 150 kmol/h flowrate)  | 25 °C/1 atm                                |
| SYNGAS      | Carbon Monoxide      |  0.45 mole fraction (of 150 kmol/h flowrate)  | 25 °C/1 atm                                |
| SYNGAS | Carbon Dioxide     |   0.05 mole fraction (of 150 kmol/h flowrate)  | 25 °C/1 atm                                |


### Blocks

| Block name  | Specifications (P/T/vap. frac.)| Other notes |
|:----------------------:|:-------------:|:-------------:|
| MIX-101 (Mixer)       | Vapor-liquid  | - |                        
| REACT (REquil)       | 20 atm/100 C/Vapor-Liquid       |   See Screenshots below for further detail  |                                
| MIX-102 (Mixer)  | Vapor-liquid       |    - |
| COOL (Heater)  | 10 C/Vapor-Liquid       |    - |
| SEP (Seperator)  | -       |    - |
| SPLIT (Splitter)  | Vapor-Liquid       |    See Screenshots below for further detail  |
| COLUMN (Radfrac)  | 10 atm       |    See Screenshots below for further detail  |



## Analysis and Discussion

## References

