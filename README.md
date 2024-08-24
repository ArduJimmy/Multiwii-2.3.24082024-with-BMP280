# Multiwii-2.3-with-BMP280
Multiwii brushed quadcopter with bmp280 module

<h1>UPDATED 24 August 2024</h1>
<p>Safety first is one of the purpose of this following changes. I made little change in Multiwii.cpp</p>

<b>Previous</b>
<code>else if (conf.activate[BOXARM] == 0 && rcSticks == THR_LO + YAW_HI + PIT_CE + ROL_CE) go_arm();      // Arm via YAW</code>

<b>After</b>
<code>
          //modified code: activating baro as soon as throttle increased and deactivating baro when arming (@ardujimmy 24 August 2024
          else if (conf.activate[BOXARM] == 0 && rcSticks == THR_LO + YAW_HI + PIT_CE + ROL_CE) {
              go_arm();
              if (rcData[THROTTLE] > THR_LO && f.BARO_MODE == 0) {
                  f.BARO_MODE = 1; // Activate BARO mode
              }
          }</code>

<h2>TESTED!</h2>
<p>All codes tested and please take this as your own risk!</p>
