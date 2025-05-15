

## **Introduction:**

The term used to correct the ideal gas law for real gases:
PV = ZnRT

Z = Z(P,T) but for reservoir engineering purposes, we usually look at Z(P) at reservoir temperature.
## **Determining Z-factor:**

Three ways to determine Z-Factor exist:
1. **Experimental Determination**
		Charge gas into a cylinder, and while knowing n, and T, vary the pressure (P) and measure the volume (V) to calculate the Z-factor.
2. **Z factor correlation of Standing and Katz**
		Calculate pseudo critical pressure and temperature of the mixture knowing its composition
$$
		p_{pc} = \sum{n_ip_{ci}}
$$
$$
		T_{pc} = \sum{n_iT_{ci}}
$$
		Then calculate pseudo reduced pressure and temperature
$$
		p_{pr} = \frac{p}{p_{pc}}
$$
$$
		T_{pr} = \frac{T}{T_{pc}}
$$
		For these pseudo reduced pressures and temperatures, these are calculated for each relevant pressure and temperature for which Z-factor is required.
		![[Standing-Katz Z-factor.png|200]]
		This assumes that non-hydrocarbon components volume fractions are are small (i.e. like 5%vol), but if larger, then corrections need to be made. If very large, like 45%, the experimental data is preferred.
		If composition data is not available, gas gravity can be used in another Standing-Katz plot/correlation to determine the pseudo critical pressure and temperatures.
3. **Direct Calculation of Z-factor**
		One method of mention is the Hall-Yarborough method which is to compute Z-factors with an EoS due to its high accuracy and ease of programming.
$$
		Z = \frac{0.06125p_{pr}te^{-1.2(1-t)^2}}{y}
$$
		p_pr = pseudo reduced pressure
		t = the reciprocal, T_pc/T
		y = the "reduced" density which can be obtained as the solution of the equation below:
		$$\begin{align}
		-0.06125p_{pr}te^{-1.2(1-t)^2}+\frac{y+y^2+y^3-y^4}{(1-y)^3}-(14.76t-9.76t^2+4.58t^3)y^2+\\(90.7t-242.2t^2+42.4t^3)y^{(2.18+2.82t)}=0
		\end{align}$$
		A walk through on how to solve this can be found in Dake's Fundamentals of Reservoir Engineering.

Z-factor can be used to calculated:
1. Gas Expansion Factor (GEF)
2. Gas Specific Gravity
3. Isothermal Gas Compressibility
4. Material Balance Analyses (such as P/Z plots)

## **Gas Material Balance:**

$$HCPV = V\phi(1-S_{wc})=\frac{G}{E_i}$$
$$Production (sc) = GIIP (sc) - Unproduced Gas (sc)$$
$$G_p = G - (HCPV)E$$
$$G_p = G - \frac{G}{E_i}E$$
$$\frac{Gp}{G} = 1-\frac{E}{E_i}$$
Finally due to being able to calculate E from the real gas law which includes the Z-factor:
$$\boxed{\frac{p}{Z} = \frac{p_i}{Z_i}(1-\frac{G_p}{G})}$$
This is the simple form of gas material balance and corrections like for HCPV changing with depletion can be done.

G_p is the produced gas and if condensate has dropped out of the gas at surface, the volume of condensate is converted to a mass, then to number of moles by knowing the molecular weight of the condensate, then the number of moles is converted using PV=nRT (since done at standard conditions) to convert to an equivalent gas production in scf and added to the actual gas production for a more accurate P/Z plot.

## **Retrograde Gas Condensate Systems:**

When reducing the pressure of a gas, the gas expands. Assuming no extraction, and constant temperature, the volume increase is estimated with PV = ZnRT assuming Z is known. This assumes the whole gas expands as a single phase.
In reality some gases that have heavy hydrocarbon contents, may not behave as a single phase gas at all pressures.
As the **dew point pressure** is reached, condensate drops out of the gas. This means for the same level of pressure depletion the gas doesn't expand as much as it might have as a single phase gas, because some of the hydrocarbon content becomes condensate instead. 

In a production setting this would mean, that while the pressure depletes so e.g. 2000psia, in a single gas phase setting, the depletion would lead to gas expansion and therefore gas production, whereas in the retrograde condensate case, some of the gas expands, and some of it becomes condensate meaning the produced gas volume for the same pressure depletion is less.

This is measured in a CVD experiment where the following equation is used to calculate the **two phase Z-factor**. 

$$Z_{2-phase}=\frac{p}{\frac{p_i}{Z_i}(1-\frac{G_p'}{G})}$$
where, G'_ p is the produced gas only, i.e. not taking into account the condensate drop out in the cylinder/reservoir. 
Since G'_ p is lower, because condensate dropped out and isn't accounted for in the production term, the denominator becomes larger, and thus the **two phase Z-factor** becomes smaller. 

**A smaller Z-factor in P/Z analysis gives a larger GIIP and the use of the two phase Z-factor in P/Z analysis of retrograde gas condensates is important for the right assessment.**

## **Isothermal Gas Compressibility:**

Isothermal gas compressibility is the following equation at constant temperature:
$$c_g = -\frac{1}{V}\frac{dV}{dp}$$
$$c_g = \frac{1}{p}-\frac{1}{Z}\frac{dZ}{dp}$$
This compressibility aims to quantify how compressible gas is at different pressures, i.e. how easily the volume of the gas changes at different pressures.

Since for a retrograde gas condensate, condensate drops out below the dew point leading to lower G'_ p (i.e. volumetric expansion as some of the gas changes phase to condensate), to them accurately describe how easily the volume of this gas changes at those pressures (i.e. the isothermal gas compressibility), the **two phae Z-factor** should be used to calculate the isothermal gas compressibility as it corrects for the P vs. V behaviour when the condensate drop out is involved and therefore more accurately defines the volumetric behaviour of the gas at pressures below dew point. **--This I am not fully sure about, so may be good to confirm with someone.**

According to ChatGPT, an EoS model can be used to calculate the compressibility of the gas phase at equilibrium with the liquid phase at each pressure step, which gives the true gas compressibility, but is only valid for the gas that is still in the system. 

## **MBAL vs. Simulators (Eclipse) according to ChatGPT (verify):**

Also according to ChatGPT, the **two phase Z-factor** is used in MBAL for Z-factor related calculations and c_g because MBAL calculates things at the bullk system level and not each phase independently like a simulator like Eclipse might. Therefore the correction to the Z-factor, i.e. the **two phase Z-factor** is needed to deal with the liquid dropout.
However, in Eclipse, the Bg term is used to convert directly between reservoir and surface volumes, and represents the Bg of the lean gas remaining in a given cell, i.e. requires the **Z-factor of the lean gas, meaning the Z-factor of the gas in equilibrium with the liquid phase at the given pressure**. 

**My personal thinking on this:**

The way to think about the single phase Z-factor of the gas in equilibrium with the liquid phase at the given pressure is to imagine that at that pressure gas and condensate have now separated. The remaining leaner gas now, can theoretically be pressured up and is theoretically at its dew point, meaning that if it's pressured up the composition of this gas doesn't change (assuming the condensate doesn't re-vaporize), and the change in volume of that lean gas can then be used to calculate the Z-factor.
If I then assume a 0.0001psi pressure increase, and observe the volume change of that gas, it is as if I measured the Z-factor at that exact pressure, because 0.0001psi is negligible. This is then the Z-factor of the single phase gas in equilibrium with the liquid phase at that pressure step.

## **PTA (according to ChatGPT):**

Same story as Eclipse/Simulators. Since PTA models how the gas phase itself compresses, and not the total fluid system and the fact that the diffusivity equation is based on gas phase properties, the single phase Z-factor and properties of the gas in equilibrium with the liquid at that given pressure should be used.