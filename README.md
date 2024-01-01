This is a copy of the ZMK 4x3 macro example.

For a bluetooth footpad you need 3 swtiches: bluetooth clear, to be able to connect to an iPad and page up & page down. There are many more keys programmed, but not connected to a switch.

The hardware connection for the swithces is defined in the boardsource3x4.overlay file (part of (https://github.com/manna-harbour/zmk/blob/zephyr-3.0/app/boards/shields/boardsource3x4/boardsource3x4.overlay):

        compatible = "zmk,kscan-gpio-matrix";
        label = "KSCAN";

        diode-direction = "col2row";

         row-gpios
            = <&pro_micro 18 (GPIO_ACTIVE_HIGH | GPIO_PULL_DOWN)>
            , <&pro_micro 19 (GPIO_ACTIVE_HIGH | GPIO_PULL_DOWN)>
            , <&pro_micro 20 (GPIO_ACTIVE_HIGH | GPIO_PULL_DOWN)>
            ;

        col-gpios
            = <&pro_micro 10 GPIO_ACTIVE_HIGH>
            , <&pro_micro 16 GPIO_ACTIVE_HIGH>
            , <&pro_micro 14 GPIO_ACTIVE_HIGH>
            , <&pro_micro 15 GPIO_ACTIVE_HIGH>
            ;
            

Thus:
BT_CLR is connected to row pin 10 & col pin 18 
PAGE_UP is connected to row pin 16 & col pin 18 
PAGE_DOWN is connected to row pin 14 & col pin 18 

A diode is connected between the switch and the col line. pins 15, 19 & 20 are left unused.

