# Handling circuits and batteries {#db-opmanual-preliminaries-electronics status=ready}

<div class='requirements' markdown="1">

Requires: Nothing

Results: Preliminary knowledge on circuits and power source properties useful in Duckietown

</div>

Duckiebots support several power bank models, although not any power will work. Here, we list properties of the supported models.

## The MOOC battery (DB-C-DBatt) {#db-opmanual-dtbattery-v2}
This battery is the standard battery for the Duckiebot Founder's edition (DB21M).

<div figure-id="fig:DB-C-DBatt_real" figure-caption="`DB-C-DBatt`">
     <img src="DB-C-DBatt_real.jpg" style='width: 20em' />
</div>

### Technical specification
- Capacity: 10'000mAh at 3.7V
- Charging: Micro USB 5V at up to 2A
- Output 2 x USB type A 5V at up to 4A (combined)
- Charge time: 0-100% takes about 5h and 0-90% about 4h with a 2A power supply
- Weight: 189g (fully charged)

### DO's
- If a battery has been subject to moisture and/or the case has been damaged eminently dispose of the battery pack.
- In case of fire use a CO2 extinguisher.
- Storage preferably in cool, dry and ventilated area which is subject to little temperature change.
- Storage at high temperatures should be avoided.

### DONT's
- Do not connect a charge voltage greater than 5V.
- Do not ocnnect an external voltage source to the USB output ports.
- The battery should not be opened, destroyed or incinerated, since they may leak or rupture. They might then release to the environment the ingredients that is contained in the hermetically sealed container.
- Do not short circuit terminals.
- Do not crush or puncture the battery or immerse in liquid.
- Do not place the battery near heating equipment, nor expose to direct sunlight for long periods.

### LED description
The battery has five LEDs used for indicating state of charge and Boot Mode.

<div figure-id="fig:DB-C-DBatt_1" figure-caption="LED indication">
     <img src="DB-C-DBatt_1.png" style='width: 25em' />
</div>

### Wake up battery
Wake up the battery (enter Idle Mode) by clicking once on the button. The state of charge LEDs will stay on for 10 seconds.

<div figure-id="fig:DB-C-DBatt_2" figure-caption="Starting the battery">
     <img src="DB-C-DBatt_2.png" style='width: 30em' />
</div>

### Charge the battery
Make sure the battery is in Idle Mode before connecting the charger. The LEDs will be flashing with 1Hz.

<div figure-id="fig:DB-C-DBatt_3" figure-caption="Charging">
     <img src="DB-C-DBatt_3.png" style='width: 25em' />
</div>

### Battery protection mode
The battery is equipped with dedicated hardware to protect its cell from low voltage discharge. This means at a certain voltage level the microcontroller together with all other active components inside the battery will be turned OFF except for the charger. In the battery protection mode the charger will "trickle" charge the battery cell until it has reached a certain safe voltage level where we will again turn on the microcontroller and LEDs. This means that for a period of up to 30 minutes the battery might not indicate a state of charge or that it is actually being charged.

## The Duckie-power-bank {#db-opmanual-dtbattery-v1}

The Duckie-power-bank (or Duckiebattery version 1) is the standard power source for Duckiebots in `DB18` and `DB19` configurations. Duckiebatteries are easily recognizable.

<div figure-id="fig:duckiebattery-front" figure-caption="The Duckie Power Bank">
     <img src="duckiebattery-front.png" style='width: 37em' />
</div>

### Overview

The Duckiebattery is equipped with 2 USB type A outputs (port A and B) and 1 Micro USB connector for charging.

<div figure-id="fig:duckiebattery-ports" figure-caption="The Duckie Power Bank ports">
     <img src="duckiebattery-ports.png" style='width: 37em' />
</div>

It also has 4 LEDs representing the state of charge. Push the button on the side of the battery pack to turn on the LEDs. The LEDs indicate the residual charge according to:

<div markdown="1">
 <col2 id='duckiebattery-charge' figure-id="tab:duckiebattery-charge" figure-caption="Duckiebattery LED charge indicators">
    <s>D1</s>                         <s>3-25%</s>
    <s>D2</s>                         <s>25-50%</s>
    <s>D3</s>                         <s>50-75%</s>
    <s>D4</s>                         <s>75-100%</s>
 </col2>
</div>

If D1 is flashing (0.5Hz) while not being charged, the battery pack is at a critical low charge ( less than 3%).

### Charging

The battery pack is charged via the Micro USB port with a 5V supply. While charging, one of the LEDs will be flashing (0.5Hz) indicating where in the charge cycle it is.

Note: When the battery pack is connected to the charger, the output voltage of port A and B will turn off for around 280ms:

<div figure-id="fig:duckiebattery-voltage-profile" figure-caption="The Duckie Power Bank ports">
     <img src="duckiebattery-voltage-profile.png" style='width: 37em' />
</div>

This is an unwanted effect which will cause the Raspberry Pi, if on, to reboot.

Note: likewise, when disconnecting the charger, the outputs will turn OFF for 20ms causing the Raspberry Pi to reboot as well.

Furthermore, while the Duckiebattery supports pass-through (both outputs A and B will function while the Duckiebattery is being charged), during charge the output voltage of port A and B will drop around 300mV which might cause an under voltage warring of the Raspberry Pi. This will put the Raspberry Pi in a throttling mode limiting its performance.

### Discharging

The output ports A and B have an unloaded output voltage around 5.1V. To turn the outputs on simply attach a load on port A/B (e.g., plug in to the Raspberry PI and duckieboard) or push the button.

The output ports will automatically turn off if less than 100mA is being drawn.

To turn the outputs back on simply push the button or reconnect the USB connector.  

The combined output current is limited to 2.8A.

The battery capacity is 7.4Ah at 5V with an efficiency as follows:

| Load  &nbsp; &nbsp; |      Efficiency &nbsp; &nbsp;     |  Autonomy &nbsp; &nbsp; |
|----------|:-------------:|------:|
| 1 A |  91% | 6h 44m |
| 1.5 A |    88%   |   4h 33m |
| 2 A | 85% |    3h 9m |
| 2.5 A | 79% |    2h 21m |
