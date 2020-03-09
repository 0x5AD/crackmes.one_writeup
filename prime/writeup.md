Reverse du binaire avec Ghidra:

Le bin est stripped, on trouve la fonction WinMain depuis l'entry point

- Une première boucle sur la saisie verif que tous les char sont entre 0x20 et 0x7e
Si ce n'est pas le cas il quitte le prog

- La deuxième boucle encode tout les char un à un avec cette fonction: (après décompilation)
    
    int _encode_func(byte const_0x81,char char_saisie,byte const_0xfb)
    
    {
        char local_1c;
        int local_8;
        
        local_1c = char_saisie;
        local_8 = 1;
        while (local_1c != '\0') {
            local_8 = (int)((uint)const_0x81 * local_8) % (uint)const_0xfb;
            local_1c = local_1c + -1;
        }
        return local_8;
    }

- Une dernière boucle xor la chaine encodé avec comme clé "Th4t's a P455W0rD"

Il nous suffis donc de prendre la chaine finale qui est comparé avec notre saisie, la unxor puis BrutForce les chars de 0x20 à 0x7e pour retrouver le mot de passe

(decode.py)

flag: Pr1me_Numb3r5_4r3_s0_P0w3rFull
