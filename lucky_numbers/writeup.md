Reverse avec GDB:

deux nombres: premier dans AL, deuxième dans BL

puis sub 0x30 pour convertir en nb

AL = AL + BL
AL = AL + 0x6 (DAA instruction)
AL = 0x16

BL = 0x38 - 0x30 = 8

AL = 0x16 - 0x6 - 0x8 = 8

le flag final est donc: 88
