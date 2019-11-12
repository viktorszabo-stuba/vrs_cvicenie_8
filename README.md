# Náplň cvičenia
- zoznámenie sa s SPI perifériou
- komunikácia s displejom ILI9163


# Konfigurácia SPI

<p align="center">
    <img src="https://github.com/VRS-Predmet/vrs_cvicenie_8/blob/master/images/spi_config.PNG" width="750">
</p>

- Mode - pri komunikácii MCU <=> displej je MCU "master" a displej je "slave"
- Hardware NSS Signal - vypnuté, "slave select" je riadený nami
- Prescaler - nastavuje frekvenciu hodín pre SPI perifériu, od toho závysí "baud rate" (SPI1 je pripojené k APB2 zbernici, ktorá má "clock" s frekvenciou 8MHz, ak pouzijeme prescaler s hodnotou 8 tak výsledná prenosová rýchlosť bude 1MBit/s)
- posielané dáta majú dĺžku 8bit
- Clock polarity - polarita "Low" - pri každom tiku hodím sa úroveň signálu zmení z "Low" na "High" a ak nie je pripojený zdroj hodin, tak je na vodiči úroveň "Low"
- Clock phase - kedy začne vzorkovanie dát a ich posúvanie

- ak cheme využívať 8 bitový prenos, je potrebné doplniť do vygenerovaného kódu nastavenie "FRXTH" v "CR2" registri :
```php
SPI1->CR2 |= 1 << 12;
```
