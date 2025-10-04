Napomena: ovaj kod je napisan da se assemble-a na load address 0x8000 (32768)

Kako radi (tehnički, kratak pregled)

Assembler kod očekuje da BASIC prije svakog poziva postavi byte na adresu KEYFLAG s bitovima:

bit0 = lijevo

bit1 = desno

bit2 = pause (space)

BASIC radi RANDOMIZE USR startAddr (ili CALL startAddr nakon LOAD "game.bin" CODE), na što se machine-code izvršava jednu iteraciju frame-a: ažurira pozicije, izračuna logiku i napiše otisak ekrana (npr. 12 redova po 32 karaktera) u text buffer na dogovorenoj memorijskoj adresi.

BASIC nakon povratka iz USR-a ispisuje sadržaj buffer-a (brzo PRINT svih redova). Zbog toga nema direktnog pisanja u ULA iz assemblera (što pojednostavljuje kompatibilnost) ali osjetno je brže i pouzdanije od čistog BASIC-a.

VAŽNO: GORNJI ASM JE PUN KOMENTARA I SKELETON LOGIKE — radi kao pouzdan template. Zbog ograničenog prostora i sigurnosti

Ako si sastavio game.bin koji se učitava INSERT u adresu 32768 (0x8000) (npr. sjasmplus catcher.asm -o game.bin), učitaj u emulator
