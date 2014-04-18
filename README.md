farmingscript
=============

$${

//Hoppers to the south in a line running east-west

//Bot goes from west to east, rows run north-south





//GETSLOTITEM(1,#id,#ss);  Looks at slot 1 in the hotbar and sets the variable #id to the id of the item

//                          and sets the variable #ss to the quantity of the item.



#north = 420;

#south = 520;

#west = -2174;

#east = -2074;



    do;

            if(%XPOS%!=#west);

                    LOOKS(180,90,1);

                    keydown(forward);

                    #cz=90909;

                    do;

                            if(%#cz%!=%ZPOS%);

                                    key(attack);

                                    wait(2t);

                                    key(use);

                                    #cz=%ZPOS%;

                            endif;

                            //for loops are mega fucked up in macro mod for some reason

                            unsafe(0);

                            GETSLOTITEM(1,#id,#ss);

                            if(%#ss%>10);

                                    slot(1);

                            endif;

                            GETSLOTITEM(2,#id,#ss);

                            if(%#ss%>10);

                                    slot(2);

                            endif;

                            GETSLOTITEM(3,#id,#ss);

                            if(%#ss%>10);

                                    slot(3);

                            endif;

                            GETSLOTITEM(4,#id,#ss);

                            if(%#ss%>10);

                                    slot(4);

                            endif;

                            endunsafe;

                    until(%ZPOS%=#south);

                    keyup(forward);

                    keydown(back);

                            wait(2t);

                    keyup(back);

                    

                    //Throw Excess Items

                    looks(180,340,1);

                    keydown(sneak);

                    wait(10t);

                    GUI(inventory);

                    FOR(#slot,1,35);

                            GETSLOTITEM(%#slot%,&item);

                            IF((&item="wheat"));

                                    wait(5t);

                                    SLOTCLICK(%#slot%);

                                    wait(5t);

                                    SLOTCLICK(-999);

                                    wait(5t);

                            ENDIF;

                    NEXT;

                    gui();

                    looks(90,0,1);

                    GUI(inventory);

                    FOR(#slot,9,35);

                            GETSLOTITEM(%#slot%,&item);

                            IF(&item="wheat_seeds");

                                    wait(5t);

                                    SLOTCLICK(%#slot%);

                                    wait(5t);

                                    SLOTCLICK(-999);

                                    wait(5t);

                            ENDIF;

                    NEXT;

                    gui();

                    LOOKS(180,90,1);

                    

                    if(HUNGER<17);

                        do(40);

                            pick("baked_potato");

                            key(use);

                        loop;

                    endif;

                    

                    keyup(sneak);

                    wait(5t);

     

                           

                                   

     

                    keydown(right);

                    #cx=%XPOS%;

                    do;

                            key(use);

                    until(%#cx%!=%XPOS%);

                    keyup(right);

                     

                    keydown(back);

                    #cz=9001;

                    do;

                            if(%#cz%!=%ZPOS%);

                                    key(attack);

                                    wait(2t);

                                    key(use);

                                    #cz=%ZPOS%;

                            endif;

                            unsafe(0);

                            GETSLOTITEM(1,#id,#ss);

                            if(%#ss%>10);

                                    slot(1);

                            endif;

                            GETSLOTITEM(2,#id,#ss);

                            if(%#ss%>10);

                                    slot(2);

                            endif;

                            GETSLOTITEM(3,#id,#ss);

                            if(%#ss%>10);

                                    slot(3);

                            endif;

                            GETSLOTITEM(4,#id,#ss);

                            if(%#ss%>10);

                                    slot(4);

                            endif;

                            endunsafe;

                    until(%ZPOS%=#north);

                    keyup(back);

                   

                    wait(5t);

                   

                    if((%XPOS%!=#west))

                            keydown(right);

                            #cx=%XPOS%;

                            do;

                                    key(use);

                            until(%#cx%!=%XPOS%);

                            keyup(right);

                    endif;

                   

                    wait(5t);

            else;

                    keydown(back);

                    keydown(left);

                    do;

                    until((%XPOS%==#east)&&(%ZPOS%==#north));

                    keyup(back);

                    keyup(left);

            endif;

    loop;

}$$
