# filecoin-energy-estimation
Tools and models for estimating Filecoin energy use from on-chain proofs

# Goals
In order to evaluate, reduce and mitigate the environmental impacts of the Filecoin network, we first need to estimate the energy use of the network. This repo contains the models we are using in order to do this. 

# Versions
Models use [semantic versioning](https://semver.org/), in which major updates (ie v X.0.0) indicate that the form of the model itself changed and requires new code to calculate energy values, minor versions (ie v 0.X.0) indicate that the methodology changed but the model itself did not, and patches (ie v 0.0.X) are simple backwards-compatible changes such as adjusting a constant.

## v1.0.0
This major version uses the following formula, derived from dimensional analysis of major sources of Filecoin energy use:

**Electrical Power = ( A * (Sealing Rate) + B * (Raw Capacity) ) * PUE**

For an entity (either the network as a whole or an individual SP):

**Electrical Power ∝ watts** is the electricity use of the entity

**A ∝ Wh/byte** is the energy required to seal a sector (sealing constant)

**Sealing Rate ∝ bytes / hour** is the rate at which new data is being sealed by that entity

**B ∝ W/byte** is the electrical power required to store data over time (storage constant)

**Raw Capacity ∝ bytes** is the amount of data stored by the entity

**PUE ∝ dimensionless** is the power usage effectiveness, which is the ratio of total electrical power consumed to that consumed by IT processes

## v1.0.1
Patch to the constant storage.max

## Benchmarks
For comparison and research, some useful resources laying out Filecoin hardware configurations and performance are:
** [Filecoin Benchmarks repo](https://github.com/filecoin-project/benchmarks)
** [Community Miner Hardware Profiles](https://github.com/filecoin-project/lotus/discussions/6071)
** [Lotus Benchmarks](https://github.com/filecoin-project/lotus/discussions/8605)
