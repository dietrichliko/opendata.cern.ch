[[stripping21r1p1 lines]](./stripping21r1p1-index)

# StrippingD2EtaHD2KEta3HMLine

## Properties:

|                |                                          |
|----------------|------------------------------------------|
| OutputLocation | Phys/D2EtaHD2KEta3HMLine/Particles       |
| Postscale      | 1.0000000                                |
| HLT1           | None                                     |
| HLT2           | HLT_PASS_RE('Hlt2CharmHadD2.\*Decision') |
| Prescale       | 1.0000000                                |
| L0DU           | None                                     |
| ODIN           | None                                     |

## Filter sequence:

LoKi::VoidFilter/StrippingGoodEventConditionCharm

|      |                                                                                            |
|------|--------------------------------------------------------------------------------------------|
| Code | ALG_EXECUTED('StrippingStreamCharmBadEvent') & ~ALG_PASSED('StrippingStreamCharmBadEvent') |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)/Particles',True)\>0 |

LoKi::VoidFilter/SelFilterPhys_StdLooseMergedPi0_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseMergedPi0](./stripping21r1p1-commonparticles-stdloosemergedpi0)/Particles',True)\>0 |

DaVinci::N3BodyDecays/D2EtaHEta3HM

|                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/[StdAllNoPIDsPions](./stripping21r1p1-commonparticles-stdallnopidspions)' , 'Phys/[StdLooseMergedPi0](./stripping21r1p1-commonparticles-stdloosemergedpi0)' ]                                                                                                                                                                                                                                                                                                                                                                                |
| DaughtersCuts    | { '' : 'ALL' , 'eta' : "(PT \> 600.0)& (ADMASS('eta') \< 60.0)" , 'gamma' : '(PT \> 600.0)' , 'pi+' : '(PT \> 500.0)& (P \> 1000.0) & (MIPCHI2DV(PRIMARY) \> 16.0)& (TRCHI2DOF \< 5) & (TRGHOSTPROB \< 0.5) & (in_range(1000.0, P, 100000.0))& (in_range(2.0, ETA, 5.0))& (PIDK-PIDpi \< 0.0)' , 'pi-' : '(PT \> 500.0)& (P \> 1000.0) & (MIPCHI2DV(PRIMARY) \> 16.0)& (TRCHI2DOF \< 5) & (TRGHOSTPROB \< 0.5) & (in_range(1000.0, P, 100000.0))& (in_range(2.0, ETA, 5.0))& (PIDK-PIDpi \< 0.0)' , 'pi0' : "(PT \> 600.0)& (ADMASS('pi0') \< 60.0)" } |
| CombinationCut   | in_range( 350.0,AM,750.0 )                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| MotherCut        | ALL                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| DecayDescriptors | [ 'eta -\> pi+ pi- pi0' ]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Output           | Phys/D2EtaHEta3HM/Particles                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                             |
|------|-------------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)/Particles',True)\>0 |

CombineParticles/D2EtaHD2KEta3HMLine

|                  |                                                                                                                                                                                                                                                                                                                                                                                    |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/D2EtaHEta3HM' , 'Phys/[StdAllNoPIDsKaons](./stripping21r1p1-commonparticles-stdallnopidskaons)' ]                                                                                                                                                                                                                                                                        |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : '(PT \> 600.0)& (P \> 1000.0) & (MIPCHI2DV(PRIMARY) \> 25.0)& (TRCHI2DOF \< 5) & (TRGHOSTPROB \< 0.5) ' , 'K-' : '(PT \> 600.0)& (P \> 1000.0) & (MIPCHI2DV(PRIMARY) \> 25.0)& (TRCHI2DOF \< 5) & (TRGHOSTPROB \< 0.5) ' , 'eta' : 'ALL' , 'pi+' : '(PT \> 600.0)& (P \> 1000.0) & (MIPCHI2DV(PRIMARY) \> 25.0)& (TRCHI2DOF \< 5) & (TRGHOSTPROB \< 0.5) ' } |
| CombinationCut   | (APT \> 2000.0)& ( in_range( 1600.0,AM,2200.0) )                                                                                                                                                                                                                                                                                                                                   |
| MotherCut        | (VFASPF(VCHI2PDOF) \< 4)& (BPVLTIME() \> 0.00025)                                                                                                                                                                                                                                                                                                                                  |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                                                               |
| DecayDescriptors | [ '[D+ -\> eta K+]cc' ]                                                                                                                                                                                                                                                                                                                                                        |
| Output           | Phys/D2EtaHD2KEta3HMLine/Particles                                                                                                                                                                                                                                                                                                                                                 |