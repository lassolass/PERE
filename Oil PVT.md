## Introduction

While gas has the ideal gas law to relate pressure, temperature and volume to each other, no simple equation such as that exists for oil. Other parameters are needed to relate surface to subsurface volumes.

**Above bubble point:**

One phase exists in the reservoir. All gas that has separated from oil at surface must originally be dissolved in the oil phase at reservoir conditions. 

**Below bubble point:**

$$q_{g@surface} = q_{free-gas} + q_{solution-gas}$$
Since gas viscosity is much lower than oil, the gas phase may flow at a much higher velocity therefore leading to a GOR that is high and that further complicates the understanding of how much gas comes from solution and how much free gas exists in the reservoir.

Following PVT parameters are used to relate surface to subsurface volumes for oil through experiments done on the reservoir oil and its dissolved gas:

* $R_s$ - Solution gas oil ratio - The volume of gas when combined with 1stb of oil will dissolve fully into the oil at reservoir conditions. Units: scf (gas) / stb (oil)
* $B_o$ - Oil Formation Volume Factor - The ratio of oil volume at reservoir versus at surface. At reservoir it includes the volume of the dissolved gas. Units: rb(oil + dissolved gas)/stb(oil)
* $B_g$ - Gas Formation Volume Factor - The volume in barrels that one scf of gas at surface will occupy at reservoir conditions. Units: rb (free gas) / scf (gas)

**Standard Conditions:** $60^o$ F and 14.7 psia (or 1 atm)

The above generally assume constant temperature and are measured vs pressure.

![[Surface vs Subsurface Oil and Gas Volumes.png|600]]

**Always keep in mind the ability to do mass balances between surface and subsurface conditions.**

For example, if the surface density of oil and gas are known, then one can do a mass balance to calculate the density of the oil at reservoir conditions and from that calculate oil gradient.

## Collection of Fluid Samples

Two main ways of collecting samples:
1. Direct subsurface sampling
2. Surface recombination of the oil and gas phases

### Subsurface Sampling

If reservoir pressure is above bubble point and $P_{wf}$ is under the bubble point too, then the sample will be at the original composition and $R_s$ should be accurate without any issue.

If reservoir pressure is at bubble point, then $P_{wf}$ is possibly below bubble point, meaning that the $R_s$ calculated is not guaranteed to be accurate, since there will have been some free gas causing an incorrect GOR.

Well conditioning is key. This means that if the reservoir pressure is above bubble point, then collect the sample under conditions where the $P_{wf}$ is not allowed to fall under the bubble point, and if it is already under bubble point, choke the well back and let pressure build in hopes of re-dissolving gas. Basically this means, do what is necessary to the well to dissolve any free gas into the oil, or to get as close to a solution GOR as possible.

If just under bubble point, there is a risk the solution GOR is slightly lower than the true solution GOR as the released gas hasn't exceeded the critical gas saturation to flow and fill the sample container.

Taking multiple samples, using a mercury injection pump at surface, the bubble point can be measured at ambient temperature, and if consistent then great, and if not, then there was an issue with sample collection.

Another important thing is determining the initial reservoir pressure and temperature.
### Surface Recombination Sampling

Oil and gas are taken at the separator and recombined to create a composite fluid sample.

Well is produced for hours until a stable GOR is observed (scf of separator gas per stock tank barrel of oil). 

Since GOR is measured as scf of gas per stock tank barrel of oil, but the sampling point of the oil is at the separator which is not at stock tank conditions, to correctly get the right ratio a shrinkage correction needs to be made for the oil from stock tank conditions back to separator conditions, so the right volume of oil is taken at the separator. 
![[Surface Recombination Sampling.png|600]]

The equation for the calculating the correct ratio of gas to oil to accurately recombine the two is the following to determine $R_{sep}$:
$$
R_{sep} [\frac{scf}{sep.bbl}] = R [\frac{scf}{stb}]S[\frac{stb}{sep.bbl}]
$$
$S$ is the shrinkage term that is calculated in the lab by placing a small volume of oil in a cell at separator temperature and pressure and flashing that oil to understand how the volume of the oil changes going down to stock tank conditions. Some gas will be liberated from the oil, but it shouldn't be an issue since from that separator oil we determine stock tank oil, which is identical to the stock tank oil measured in the real facilities (where gas will also be liberated further). Therefore it's a like for like comparison, therefore meaning that the calculated ratio of gas to oil is correct for sampling purposes. 

**It is important for the engineer to measure and know these pressures and temperatures and communicate them to the lab.**

**To ensure the sample is good, ideally the $P_{wf}$ should be above bubble point for the sampling, and by extension, the sample should be taken as early as possible in the well/field life to ensure the highest chance of this.**

## Determination of Basic PVT parameters in lab and conversion for field operating conditions

For the three basic parameters the following will be needed:
1. Flash expansion of the fluid sample to determine the bubble point pressure
2. Differential expansion of the fluid sample to determine the basic parameters $B_o$, $R_s$, and $B_g$. 
3. Flash expansion of the fluid samples through various separator combinations to enable the modification of laboratory derived PVT data to match field separator conditions.

### Flash Expansion for Bubble Point

The PV cell in which the testing is done is shown below:
![[PV Cell schematic.png|600]]

As the pressure is reduced, a significant change in compressibility is felt when bubble point is reached due to the presence of gas.

At each pressure step total fluid volume is measured $v_t$. It is defined with respect to the volume at bubble point, meaning $v_t$ = 1.0 at bubble point. $v_t = v/v_b$, where $v_b$ is the fluid volume at bubble point.

![[Flash Expansion Schematic.png|300]]

An example results table of a such experiment is shown below:
![[Isothermal Flash Expansion Example Results.png|300]]

Other PVT parameters can't be calculated with the flash expansion data, and differential liberation is used for those. 

### Differential Liberation for other Parameters

As the pressure is dropped and gas is released from the oil, the gas is removed from the PV cell leaving only oil. The volume of the gas released is measured relative to the volume of oil at bubble point, and the oil volume also continues to be read in the same way relative to the oil volume at bubble point.

![[Differential Liberation Schematic.png|300]]

The gas that is liberated is then allowed to expand to stock tank conditions and is then re-measured as $V_g$ rather than $v_g$. Oil volume is measured as $v_o$. $F$ is then the cumulative amount of liberated gas at standard conditions measured relative to the volume of oil at bubble point. $E$, the gas expansion factor is then calculated by the following: $V_g / v_g$. [[Z-factor]] can be calculated by solving the following equation: $Z = \frac{p}{p_{sc}}\frac{T_{sc}}{T}\frac{1}{E} = 35.37\frac{p}{ET}$.

![[Isothermal Differential Liberation Example Results.png|600]]

For high volatility oils the oil volumes from flash expansion and differential liberation are different as flash expansion is at constant composition, whereas differential liberation is at changing composition, and sequentially heavier compositions due to the release of gas.

For low volatility oils mainly saturated with methane and ethane, the oil volumes are virtually the same in both experiments.

Oil volume will generally be lower in the flash expansion as the presence of gas makes it easier for the oil to change phase.

Differential liberation better describes the separation of oil and gas as in reality the different velocities mean that oil and gas are generally not in equilibrium in real life conditions, with the exception of the brief period of lower GOR right below bubble point due to critical gas saturation not being reached yet.

### Accounting for Separator Conditions

A separator acts as a place where flash expansion occurs as the oil is allowed to sit in equilibrium with the gas for a while. If two or more separators are used then gas is removed in the first separator and the oil is again flashed in the second separator. This physical isolation corresponds to differential liberation. This also makes multi-stage separation more desirable since it allows the final oil volume to be larger than if the oil was flashed. 

**The volume of equilibrium oil collected in the stock tank is dependent on the manner in which the oil and has are separated. This also means that $B_o$ and $R_s$ parameters, which are measured with respect to stock tank volumes must also be dependent on the manner of surface separation and cannot be assigned absolute values.**

To test the separator effects, bubble point oil at reservoir temperature is passed to a PV cell which is connected to a single stage or multi-stage separation system. Each separator is at a different pressure and temperature. Bubble point oil is then flashed through the separation system and resulting volumes of oil and gas are calculated.

![[Separator Flash Expansion Example Results.png]]

The $c_{b_f}$ is the volume of oil collected in the stock tank relative to the bubble point oil initially charged into the PV cell. The "f" subscript indicates that this was done under flash conditions. Even though multi-stage separation is closer to differential liberation, it's still subscripted with "f" as it really doesn't matter since these numbers are determined experimentally anyway.

$R_{si_f}$ is the initial solution gas oil ration corresponding to the separators used and is measured in the experiments in scf/stb.

**The differential liberation data explains and shows the volumetric behaviour of the oil in the reservoir and the separator flash data account for the volume changes between reservoir and stock tank.**
	Basically when pressure changes in the reservoir the DL data helps explain those changes, but when wanting to relate those volumes back to surface stock tank barrels, the separator flash data is needed.

### Calculating Field Level PVT Parameters

$v_o$ is measured ($rb/rb_b$) and $c_{b_f}$ is measured ($stb/rb_b$), therefore to calculate $B_o$ the following is done:

$$
\boxed{B_o[\frac{rb}{stb}] = \frac{v_o}{c_{b_f}}[\frac{rb/rb_b}{stb/rb_b}]}
$$
This basically means at some pressure the volume of oil will be $v_o$ relative to the bubble point volume. What happens to that volume at stock tank depends on the separator conditions, which is defined by $c_{b_f}$. 

To calculate $R_s$ the following equation is needed:
$$
\boxed{(R_{si_f} - R_s)[\frac{scf}{stb}] = F[\frac{stb}{rb_b}]5.615[\frac{scf}{stb}]\frac{1}{c_{b_f}}[\frac{rb_b}{stb}]}
$$
$R_{si_f}$ is the maximum gas dissolved in the oil, i.e. the GOR above bubble point, and it is the initial solution GOR and it is also a parameter determined during the separator flash experiments. At a lower pressure particularly below bubble point, the solution GOR is lower, and is $R_s$. The difference between the two is how much gas was liberated therefore. This value is $F$ as it is the measured standard gas volume released cumulatively at a given pressure. This number is relative to oil volume at bubble point pressure though (and also determined from the DL test without taking the separator flashing into account), so needs to be corrected by $c_{b_f}$ to correct that happens in the separator. 

Finally $B_g$ is calculated simply as follows:

$$
B_g [\frac{rb}{scf}] = \frac{1}{E}[\frac{rcf}{scf}]\frac{1}{5.615}
[\frac{rb}{scf}]$$

If separator conditions change during the life of the field, then the differential liberation data will have to be adjusted with the new $c_{b_f}$ and $R_{si_f}$ numbers for the new separator setup.

**Dodson's PVT analysis technique** flashes the oil to stock tank conditions through the given separator setup at each unique pressure step giving a direct measurement of $B_o$ and $R_s$. This requires a lot of samples and the above method is a reasonable approximation at least for low and moderate volatility oils.


### Alternative Manner of expressing PVT Laboratory Analysis Results

Sometimes instead of using the $c_{b_f}$ value from the separator experiment to correct DL data into field level PVT parameters, labs use the "residual oil volume", which is the volume of oil at standard conditions from the DL experiment as a reference volume. This volume depends on the number of pressure steps taken, so the data using this volume as the reference is not absolute the same way that it is when the bubble point oil volume is used as the reference.

If $c_{b_d}$ is 0.7794, then it is 0.7794 stb-residual oil / 1$rb_b$. I.e. it is 0.7794 stb of residual oil that remains compared to the 1 barrel of oil that existed at bubble point. By then dividing $v_o$ by this number, one gets a value with units $[\frac{rb}{stb-residual-oil}]$, and not $\frac{rb}{stb}$ as separator flashing is not taken into account yet.

$$
B_{o_d} = \frac{v_o}{c_{b_d}}[\frac{rb/rb_b}{stb-residual/rb_b}]
$$
$$
(R_{si_d} - R_{s_d})[\frac{scf}{stb-residual}] = F[\frac{stb}{rb_b}]5.615[\frac{scf}{stb}]\frac{1}{c_{b_d}}[\frac{rb_b}{stb-residual}]
$$
$$
R_{si_d} = 5.615\frac{(MaxValueOfF)}{c_{b_d}}[\frac{rb_b}{stb-residual}]
$$

For some cases like low volatility oils, these may be close enough to the real values of solution GOR and FVF for oil, but for moderate to high volatility oils there will be an error and the necessary correction for separator flash needs to be done. This would be done the following way when the lab results are presented as above using the $c_{b_d}$ figure.

$$
\boxed{B_o = \frac{v_o}{c_{b_f}} = \frac{v_o}{c_{b_d}}[\frac{c_{b_d}}{c_{b_f}}] = B_{o_d} [\frac{B_{ob_f}}{B_{ob_d}}]}
$$
$$
R_s = R_{si_f} - \frac{5.615F}{c_{b_f}} = R_{si_f} - \frac{5.615F}{c_{bd_f}}[\frac{c_{b_d}}{c_{b_f}}]
$$
$$
\boxed{R_s = R_{si_f} - (R_{si_d}-R_{s_d})[\frac{B_{ob_f}}{B_{ob_d}}]}
$$
In the above equations the following parameters are defined as following:

$R_{si_f}$ = solution GOR of bubble point oil determined by flashing the bubble point oil through the given separator conditions to stock tank conditions.

$R_{si_d}$ = solution GOR of bubble point oil determined during the differential liberation experiment and measured relative to the residual oil volume at $60^oF$ and 14.7 psia. This is therefore the total volume of gas in scf per the residual volume of oil at standard conditions at bubble point. 