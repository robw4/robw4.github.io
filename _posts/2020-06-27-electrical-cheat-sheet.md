---
layout: post
author: robw
title: Electrical Engineering
abstract: "Together Maxwell's equations and the Lorentz force equation constitute the foundation of electrical engineering. Remarkably these five equations are enough to describe most of the electronics we experience every day."
image: /assets/images/electrical.jpg
numbered: false
---

## Classical Electromagnetism

Together Maxwell's equations and the Lorentz force equation constitute the foundation of electrical engineering. Remarkably these five equations are enough to describe most of the electronics we experience every day.

![Teaser](/assets/images/electrical.jpg)
_A figure caption_

Lorentz equation
: The total force experienced by a charge moving through an electric field of strength $\boldsymbol{E}$ (V / m = F / q) and magnetic field $\boldsymbol{B}$ is given as $$\boldsymbol{F} = q \boldsymbol{E} + q \boldsymbol{v} \times \boldsymbol{B}$$. From the lorentz equation a wire carrying current $i$ at an angle $\theta$ to a magnet field $B$ will experience a force equal to $F = Bil \sin \theta$.

Gauss's Law
: The total amount of electric flux $\Phi_{E}$ passing through the closed boundary $\partial \Omega$  of volume $\Omega$ is proportional to the total charge $Q$ contained within it, $$\Phi_{E}= Q/ \epsilon $$ where $\Phi_{E} :=\oint_{\partial \Omega} \mathbf{E} \cdot \mathrm{d} \mathbf{S}$ and $Q := \iiint_{\Omega} \rho \mathrm{d} V$. The constant $\epsilon$ is the *permittivity* of the medium and is often expressed as $\epsilon = \epsilon_0 \epsilon_r$ where $\epsilon_0$ is the *permittivity* of free space. This equation can alternatively be expressed in terms of the *electric displacement field* or *D-field* $\mathbf{D} := \epsilon \mathbf{E}$.  For a field of strength $E$ passing normally through an area $A$ the electric flux density is given by $\Phi_{E} = EA$.

Ampere's circuit Law
: The line magnetic field along a contour $\partial \Sigma$ enclosing area $\Sigma$ is proportional to the total current passing through it. $$\oint_{\partial \Sigma} \mathbf{B} \cdot \mathrm{d} \boldsymbol{l} = \mu I$$. The constant $\mu$ is the *permeability* of the medium often expressed as $\mu = \mu_0 \mu_r$. The current $I$ is composed of two parts $I = I_c + I_d$ with  conductive current $I_c :=\iint_{\Sigma} \mathbf{J} \cdot \mathrm{d} \mathbf{S}$ and *displacement* current $I_d := \epsilon \frac{\mathrm{d}}{\mathrm{d} t} \iint_{\Sigma} \mathbf{E} \cdot \mathrm{d} \mathbf{S}$. Alternatively this can be written in terms of the *H-field* as $\mathbf{B} = \mu \boldsymbol{H}$. The conductive current corresponds to the actual movement of free charges whilst the displacement current results from changes in the magnetic field (for example the current flowing in a capacitor).

> The displacement current is needed to satisfy continuity of current $\nabla \cdot \mathbf{J}=-\frac{\partial \rho}{\partial t}$ and to allow electromagnetic waves to propagate through free space when $\mathbf{J} = \mathbf{0}$

Maxwell-Faraday equation
: The electromotive force $\epsilon$ induced around a contour is proportional to the time rate of change of magnetic flux flowing through it, $$\epsilon(t) = -\frac{\mathrm{d}}{\mathrm{dt}} \Phi_{B}(dt)$$ with,$\Phi_{B} :=\iint_{\Sigma} \mathbf{B} \cdot \mathrm{d} \mathbf{S}$ and  $\epsilon := \oint_{\partial \Sigma} \mathbf{E} \cdot \mathrm{d} \boldsymbol{l}$. For a magnetic flux of strength $B$ passing normally to an area $A$ the magnetic flux reduces to $\Phi_{B} = B A$.

Gauss's Law for Magnetism
: The total magnetic field passing through a *closed surface*  $\partial \Omega$ is zero $$\oint_{\partial \Omega} \mathbf{B} \cdot \mathrm{d} \mathbf{S}=0$$. As a result magnetic monopoles do not exist and magnetic field lines never begin or end but must form loops.

> This is an important result in its own right even if it isn't typically applied

## Foundations

Electric Potential
: _Electrical potential_ is the electrical potential energy $\Delta U$ per unit charge between two points. We consider the electric potential gained by unit charge as an electromotive force $\epsilon = \Delta U / q$ and the electric potential lost by each charge as a potential drop $v =  -\Delta  / q$. It is measured in $\text{V} = \text{JC}^{-1}$.

Current
: Current is the rate of change of charge flowing through a circuit $i = dq / dt$. An electromotive force applies to a conductor will cause a current to flow.

Power
: The power $p = v i$ dissipated by a circuit element is equal to the product of current flowing to it and potential difference across it

Conductance
: In an electric field charge carriers will experience a force and will accelerate up to an average drift velocity $v = \mu \epsilon$.

Under an electric potential difference $\epsilon$

## Linear Circuits
### Linear Devices
The electrical properties of a linear device do not change with the voltage applied / current flowing to it. Resistors, inductors, capacitors and power sources are all linear devices.

Resistors
: The current flowing through an ohmic resistor is proportional to the electromotive force applied to it $$\epsilon = iR$$ (ohms law) where $R$ is the resistance of the component measured in ohms ($\Omega$). The resistance of a wire of length $l$, area $A$ and *resistivity* $\rho$ can be calculated as $R = \rho l / A$. Resistors in series can be combined as $R = \sum_k R_k$ and in parallel as $1/R = \sum_k 1/R_k$.

Inductors
: A time-varying current $i(t)$ flowing through an inductor creates a time varying magnetic field and induces a back emf $\epsilon(t)$ opposing the flow of current $$\epsilon(t) = - L \frac{d i}{ dt} \implies v(t) = L \frac{d i}{ dt}$$. The constant $L$ is the inductance typically deduced from geometry of the inductor (using faradays law) and is given by $L = \Phi / i$ where $\Phi$ is the total amount of magnetic flux flowing through the inductor. The inductance of a solenoid of area $A$, length $l$ and turns $n$ is given by $L = \mu A N^2 / l$.

Capacitors
: The amount of charge stored by a capacitor is proportional to the voltage applied across it $Q= CV$ where $C$ is *capacitance* measured in Farads typically calculated from the geometry of the capacitor (using gauss's law). For a constant $C$ the current flowing through a capacitor is related to the potential difference across it as $$i(t) = C \frac{dv}{dt}$$

Power Sources
: An ideal voltage source is able to supply the same voltage to a circuit independent of the current drawn from it whilst an ideal current source is able to supply the same current to a a circuit independent of the potential difference across. Non-ideal voltage sources can be modelled as an ideal voltage source in series with a resistor and non-ideal current sources as an ideal current source in parallel with a resistor.

Coupled Inductors
: A time-varying current $i_1(t)$ flowing through one inductor, induces a back emf in any inductor on the same magnetic circuit of magnitude equal to $$\epsilon_2(t)= \pm M \frac{d i_1}{ dt}$$. The constant $M$ is the mutual inductance $M=\Phi_{12} / i_1 = \Phi_{21} / i_2$ where $\Phi_{12}$ is the total amount of magnetic flux flowing through the 2nd inductor resulting from the first. The sign of this back emf is inferred from Amperes and Faradays law.

### Linear Circuits
Any circuit which obeys the principle of superposition is linear. It is composed of only linear circuit components.
> This does not mean that the circuit is composed of only affine functions. Typically a circuit will be characterised by a set of ordinary differential equations.

Superposition
: The output of a circuit $f(x)$ for linear combination of signals $x =a x_{1} + b x_{2}$ is given by $$F\left(a x_{1}+b x_{2}\right)=a F\left(x_{1}\right)+b F\left(x_{2}\right)$$ the weighted sum of its response to each signal.

For any linear circuit kirchoff's law's hold:

Kirchoff's Law's
: Kirchoff's current law ($\sum_k i_k = 0$) states that the total current flowing into a node must sum to 0. Kirchoff's voltage law ($\sum_k v_k = 0$) states that the summed potentials along any closed loop must sum to $0$.

### DC Circuit Analysis
Norton / Thevenins Equivalence
: Any combination of resistors, voltage sources and current sources can be replaced with a single voltage source $V_{eq}$ in series with a resistor $R_{eq}$ (Thevenin's theorem) or a current source $I_{eq}$ in parallel with $R_{eq}$ (Norton's theorem). Defining the open circuit voltage $V_{oc}$ as the potential difference across the output terminals of a network (circuit) without any load applied and the short circuit current $I_{sc}$ as the current flowing between the output terminals when connected with an ideal wire $V_{eq}=V_{oc}$, $I_{eq}=I_{sc}$  and $R_{eq} = V_{oc} / I_{sc}$. Alternatively, if the current and voltage sources are not dependent on any other current or voltage in the circuit, $R_{eq}$ can be found by replacing all current sources with open circuits, short circuiting all voltage sources, and calculating

Power Matching
: The maximum power is drawn from a power supply / network when the load resistance is matched to the internal resistance of the power supply / network corresponding to half the power being dissipated to the power supply, half to the load resistance and a resulting efficiency of $50\%$.

### AC Circuit Analysis
In AC circuit analysis we are interested in the response of a circuit to a steady-state signal of the form $x(t) = X_p \cos( \omega t + \alpha)$ where $\omega$ is the frequency measured in $\text{rad} \text{s}^{-1}$, $\alpha$ is the phase offset and and $X_p$ is the peak amplitude of the wave. The average root mean square of an AC signal $X_{rms} = 1 / T \int x(t) dt = X_p / \sqrt{2}$.

Phasors
: For a linear circuit superposition holds; instead of analysing a circuits response to $x(t)$ we analyse the circuits response to $\hat{X}(j\omega t) = \sqrt{2} X e^{j \omega t}$ considering the real part of the solution only. This allows AC signals to be summarised by the complex phasor $X = \|X\| e^{j \alpha}$. The magnitude of this phasor gives the rms value of the signal (by convention) whilst its argument gives the phase offset.

Impedance
: The impedance $Z$ of a component relates the AC current $I(j\omega)$ to the potential difference applied to it $V = IZ$. For a resistor $Z = R$, for a capacitor $Z=1 / j \omega C$ and for an inductor $Z = j \omega L$. The impedance of circuit components in parallel and in series are combined as $Z = \sum_i Z_i$ and in parralel as $1 / Z = \sum_i 1 / Z_i$. The general impedance for a combination of components is given as $Z=R + jX$ where $R$ is *resistance* and $X$ is *reactance*.

> For a capacitor the complex impedance is derived by considering a $V(j \omega) =  1 / C \int I dt = 1 / C \int \|I\| e^{j \omega t} dt = I(j \omega) / j \omega C$ giving $Z=1 / j \omega C$. Likewise for an inductor $V(j \omega) = L \ d / dt \{ \|I\| e^{j \omega t} \}$ giving $Z = j \omega L$.

Norton / Thevenin's theorem
: Norton's and thevenin's theorem hold and equivalent circuits are derived in the same way as for DC with resistances replaced with complex impedances.

Instantaneous Power
: For phasors $V=\|V\|\exp(j\phi)$, $I=\|I\|$  and network impedance $Z=R+ jX=\|Z\| \exp(j \phi)$ the power phasor is given as $$\hat{P} = V^* I = P + jQ$$ where $P= \|I\| \|V\| \cos \phi$ is the real power dissipated in the circuit measured in Watts ($\text{W}$) and $Q= \|I\| \|V\| \sin \phi$ is the (peak) reactive power measured in Volt-Amperes ($\text{VA}$). They are equivalently expressed as
$P = \|I\|^{2} R =  \|V\|^{2} / R$ and $Q = \|I\|^2 X = \|V\|^{2}  / X$.  The instantaneous power is given as $p(t) = P (1+\cos2wt) - Q  \sin 2 \omega t$.

Power Matching
: For internal impedendence $Z_s = R_s + j X_s$ and load impedence $Z_l = R_l + j X_l$ the maximum power is delivered to a load $Z_l = Z_s^*$ if $Z_s$ can be chosen freely, $R_l = \|Z_s\|$ if $X_l = 0$ or $R_l = \sqrt{R_s^2 + (X_s + X_l)^2}$ if $X_l$ is fixed.

Coupled Inductors
: A voltage source with  phasor $V=\pm j \omega M I'$ is added in series to every coupled inductor where $I'$ is the current phasor flowing through its partner. The polarity of $V$ is determined using dot notation:  a current $I'$ entering / leaving the dotted terminal of one inductor induces $V$ in the second referenced positive to the seconds dotted/ un-dotted terminal.

Frequency Response
: The frequency response of an AC circuit is characterised by the *transfer function* $G(j \omega) :=  X_{o}(j \omega) / X_{i}(j \omega)$ which for linear systems is given by $G(j \omega) = K\prod^L_l(jw - z_l) / \prod^D_d (j \omega - p_d)$ where $D \geq L$. The *zeros* $z_l$ give $G(j \omega) = 0$ whilst the poles $p_d$ give $G(j \omega) = \infty$. $K$ is referred to as the gain of the system. The *order* of a a system is given by the degree of the denominator (the number of poles) and is equal to the number of independent energy storage elements in the circuit.

Bode Plots
: By plotting $G_{db} := 20 \log_{10} \| G(j \omega)\|$ and $G_{\phi} := \text{arg} \{G(j \omega) \}$ on a log axis of frequency $\omega$ the frequency response of a system can be visualised. $G_{db}$ is the frequency dependent gain of the system (in decibels) and $G_{\phi}$ is the phase shift. For linear systems $G(j \omega)$ can be written as $G(j \omega) = \prod_l g_l(j \omega) / \prod_d g_d(j \omega)$ with $g(j \omega) = 1 \pm j \omega / \hat{\omega}$ and the bode plots for gain and phase can be constructed through the superposition of each $g_{db}$ and $g_{\phi}$ as $G_{db / \phi} = \sum_l g_{db /\phi}^{(l)} -  \sum_d g_{db / \phi}^{(d)}$. Each $g_{db}$ corresponds to a straight line of gradient $20 \ \text{db dec}^{-1}$ starting at $\hat{\omega}$. Each  $g_{\phi}$ corresponds to a straight line with gradient $\pm \pi / 4 \  \text{rad dec}^{-1}$ starting at $(0.1 \hat{\omega}, 0)$ and ending at  $(10\hat{\omega}, \pi / 2)$. At $\omega = \hat{\omega}$, $g_\phi= \pi /4$ and $g_{db} =3 \text{db} \implies \|g({j \omega})\| = 1 / \sqrt{2}$.



## Active circuits
### Quantum Theory
Bound States and Discrete Energy Levels
: A particle subjected to a potential such that the particle has a tendency to remain localised in one or more regions of space is in a *bound state*. Particles in a bound state can only take on certain discrete values of energy.
> Eg. chemical bonds, protons and neutrons all correspond to bound states

Pauli Exclusion Principle
: Two or more identical fermions cannot occupy the same quantum state within a quantum system simultaneously.

## Semi Conductors
Conductance and ohms Law
: Under an applied electric field $\boldsymbol{E}$ charges will experience a force equal to $\boldsymbol{F} = q \boldsymbol{E}$ (lorentz) and if they are unconstrained accelerate. But t


Charge Carriers in semi-conductors
: Under an electric field $\epsilon$ free charges will experience a force $F = q \epsilon$ and will on average be accelerated to a drift velocity $v = \mu \epsilon$.

Semi-Conductors and the Bond Model
: In an electric field $\epsilon$ free charges will drift with velocity $v = \mu \epsilon$ where $\mu$ is a material property known as *mobility*. The total current is given as, $$J =J_n + J_p = (qn \mu_n + q p \mu_p) \epsilon \implies \sigma = q(n\mu_n + p \mu_p)$$ where $\sigma$ is the *conductivity*. *Intrinsic* semi-conductors have one hole per free electron such that $n_i = p_i$.

Band Theory
: As a result, the electron energy levels of a lattice of atoms will split and merge forming bands of allowed energy levels. At $T=0K$ every state within the *valence band* will be completely occupied by electrons and the next highest energy level the *conductance band* will be completely free of electrons.  The energy gap $\Delta E = E_c - E_v$ is the difference between the lowest energy state in the conductance band $E_c$ and the highest energy state in the valence band $E_v$.  At temperatures above absolute zero the probability that a particular energy level $E$ will be occupied by an electron in a system at thermal equilibrium is given by a Femi-Dirac distribution $$F(E) = \frac{1}{e^{(E - E_f)/k_BT} + 1}$$ where $E_f$ is the fermi-level corresponding to $F(E)=0.5$ for all temperatures.


as two atoms in a lattice are brought together, there energy levels split generating to allow for

Band Theorem
: As a result of the pauli exclusion principle multiple



### Current
Electric charges in a an electrical field experience a force $F=qE$ if electrons are free to move this will cause


The electric-field





### Semi Conductors


Energy Bands
: Quantum energy



Free Charges
: Due to the thermal excitement of a material at any one time there will be a net number of delocalised electrons and holes. Under an electric current

At any time the random thermal excitement of electrons leads to a net number of free electrons $n$ and positively charged holes $q$.

The random thermal excitement of electrons in bonds results in

The random thermal excitement of electrons in bonds results in a net number of free electrons $n$ and positively charged ions $p$ per unit volume at any instance in time.







Extrinsic semi-conductors are interlaced

