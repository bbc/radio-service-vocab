radio-service-vocab
===================

A RDF vocabulary for describing Radio Stations.

_This document is Work in Progress and is still being updated._

It is heavily based on [TS 103 270 - RadioDNS Hybrid Radio] and [TS 102 818 – Service and Programme Information] - aka RadioEPG.
It is also influenced by the [BBC Programmes Ontology].

## Examples

* [BBC 6 Music](https://github.com/bbc/radio-service-vocab/blob/master/examples/bbc_6music.ttl) (a UK national, DAB only)
* [BBC London](https://github.com/bbc/radio-service-vocab/blob/master/examples/bbc_london.ttl) (a Local service, single FM + DAB)
* [BBC Five Live](https://github.com/bbc/radio-service-vocab/blob/master/examples/bbc_radio_five_live.ttl) (a UK national, AM + DAB)
* [BBC Radio Four](https://github.com/bbc/radio-service-vocab/blob/master/examples/bbc_radio_four.ttl) (a UK national, multi-service, lots of FM frequencies, AM and DAB)
* [BBC World Service](https://github.com/bbc/radio-service-vocab/blob/master/examples/bbc_world_service.ttl) (Shortwave with Amplitude modulation signalling system)
* [KCSN](https://github.com/bbc/radio-service-vocab/blob/master/examples/kcsn.ttl) (US local Radio Station on FM and HD Radio)

## Entity Types

### Service

An individual Radio Service, also known as a Radio Station.

**Properties**

| Property   | Expected Type | Description                                  |
|------------|---------------|----------------------------------------------|
| shortName  | Text          | The name of the service (max 8 characters)   |
| mediumName | Text          | The name of the service (max 16 characters)  |
| longName   | Text          | The name of the service (max 128 characters) |
| genre      |               |                                              |
| keywords   |               |                                              |
| beaerer    |               | A service should have one or more Bearers.   |


### Bearer

An individual transmission mechanism for a Radio Service.
May be analogue, digital or an online stream.
An analogue bearer must be on a single frequency, a digital bearer might be part of a multiplex.

**Properties**

| Property  | Expected Type | Description                                                                                                                                            |
|-----------|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| cost      | Integer       | An indication of a relative 'cost' of acquiring the service from the service provider.                                                                 |
| mimeValue | Text          | Indicates the MIME type (RFC 2045) of the audio carried by the bearer.                                                                                 |
| bitrate   | Integer       | Bitrate of the audio carried by the bearer, in kilobits per second (kbps).                                                                             |
| offset    | Integer       | An indication of the offset given to the audio on this bearer by the service provider, in milliseconds relative to other bearers for the same service. |


### BearerAM

Sub-class of a generic bearer for AM (Amplitude Modulation) broadcasts.
AM radio stations typically broadcast in medium wave band but also in parts of the longwave and shortwave spectrum.

**Properties**

| Property  | Expected Type | Description                                                                                                                                            |
|-----------|---------------|---------------------------------------------|
| frequency | Integer       | The frequency of the broadcast in kHz       |

### BearerDAB

Sub-class of a generic bearer for DAB (Digital Audio Broadcasting) and DAB+.

### BearerDRM

Sub-class of a generic bearer for DRM (Digital Radio Mondiale).

### BearerFM

Sub-class of a generic bearer for FM (Frequency Modulation) broadcasts.
FM radio stations use the VHF frequencies, typically in the range 87.5 to 108.0 MHz.

**Properties**

| Property  | Expected Type | Description                                                                                                                                            |
|-----------|---------------|---------------------------------------------|
| frequency | Float         | The frequency of the broadcast in MHz       |

### BearerIBOC

Sub-class of a generic bearer for IBOC (In-band on-channel), also known as HD Radio.

**Properties**

| Property       | Expected Type | Description                                                                                                                                            |
|----------------|---------------|------------------------------------------------|
| frequency      | Float         | The frequency of the broadcast in MHz          |
| channel        | Integer       | The channel number                             |
| transmissionId | Integer       | In the US this is the FCC assigned facility ID |



[BBC Programmes Ontology]: http://purl.org/ontology/po
[TS 103 270 - RadioDNS Hybrid Radio]: http://www.etsi.org/deliver/etsi_ts%5C103200_103299%5C103270%5C01.02.01_60%5Cts_103270v010201p.pdf
[TS 102 818 – Service and Programme Information]: http://www.etsi.org/deliver/etsi_ts/102800_102899/102818/03.01.01_60/ts_102818v030101p.pdf

