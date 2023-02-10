# kiss-tuning
storage spot for krunked kiss tunes 

I wanted a better place to store the UTLRA tunes than just on discord. <br><br>
so i uploaded them here for immdiate use!<br>
do not try and restore these files into the GUI; they currently will not work.<br><br>

# how to use 
Before proceeding -- please note that this section's PID's are meant for the kiss ultra v1.
if you are here for kiss ultra v2 settings, scroll down to the <a href="https://github.com/krunked-fpv/kiss-tuning#ultra-v2-tuning">ultra-v2-tuning</a> section.
all of the principles still apply. but with new numbers and a few changed settings.

Use the following PID's as 3 step process to triangulate the best RANGE for your quad.

1. start at the ULTRA defaults
    -- should fly great on almost any quad
2. try the high D
    -- if it TRILLS or makes bad noises, you know that high D is too high
3. try the low D
    -- if the quad bounces back harshley or has bounceback, you now know your quad will want more D. 

<img src="https://github.com/krunked-fpv/kiss-tuning/blob/main/krunked_default.jpg?raw=true" width="660" height="275"/><br>
<img src="https://github.com/krunked-fpv/kiss-tuning/blob/main/krunked_high_D.jpg?raw=true" width="660" height="275"/><br>
<img src="https://github.com/krunked-fpv/kiss-tuning/blob/main/krunked_low_D.jpg?raw=true" width="660" height="275"/><br>



# ultra-v2-tuning
kiss ultra v2 golden pids

1. kiss ultra v2 is a requirment
2. experimental mode must be ON for these to work
3. TPA setting is changed to give authority back at low throttle and kill some mid throttle oscillations 
3. if you have issues with these settings, return to ultra defaults
4. Flight performance tab maxed out -- becuase we do all the things ultra

ADVANCED TUNING NOTE:

you can use higher pd gain's than pictured, remember this is a 'golden' tune.. use the below numbers as a starting point and use the ratio of 1p:3.5d, and you'll find that on the cleanest builds youll be able to push the pd gains up near a 2.0 multiplyer;  your mileage may vary based on a lot of factors so raise your pd gains from the golden starting point at your own risk

<div class="pid-table" id="tune1">
    <h4>PIDs & Rates - Tune 1</h4>
    <input type="hidden" class="max-p" value="10">
    <input type="hidden" class="max-d" value="30">
    <input type="hidden" class="pd-ratio" value="3.5">
    <table>
        <tr>
            <th></th>
            <th>P</th>
            <th>I</th>
            <th>D</th>
            <th>RC Rate</th>
            <th>Rate</th>
            <th>RC Curve</th>
        </tr>
        <tr>
            <td>Roll</td>
            <td><input type="number" class="roll-p" step="0.1" data-ogvalue="3.2"></td>
            <td><input type="number" class="roll-i" step="0.001" value="0.045"></td>
            <td><input type="number" class="roll-d" step="0.1" data-ogvalue="18.5"></td>
            <td><input type="number" class="roll-rc-rate" step="0.1" value="1.45"></td>
            <td><input type="number" class="roll-rate" step="0.1" value="0.65"></td>
            <td><input type="number" class="roll-rc-curve" step="0.1" value="0.22"></td>
        </tr>
        <tr>
            <td>Pitch</td>
            <td><input type="number" class="pitch-p" step="0.1" data-ogvalue="3.8"></td>
            <td><input type="number" class="pitch-i" step="0.001" value="0.055"></td>
            <td><input type="number" class="pitch-d" step="0.1" data-ogvalue="20.5"></td>
            <td><input type="number" class="pitch-rc-rate" step="0.1" value="1.45"></td>
            <td><input type="number" class="pitch-rate" step="0.1" value="0.65"></td>
            <td><input type="number" class="pitch-rc-curve" step="0.1" value="0.22"></td>
        </tr>
        <tr>
            <td>Yaw</td>
            <td><input type="number" class="yaw-p" step="0.1" value="8"></td>
            <td><input type="number" class="yaw-i" step="0.001" value="0.05"></td>
            <td><input type="number" class="yaw-d" step="0.1" value="5"></td>
            <td><input type="number" class="yaw-rc-rate" step="0.1" value="1.45"></td>
            <td><input type="number" class="yaw-rate" step="0.1" value="0.65"></td>
            <td><input type="number" class="yaw-rc-curve" step="0.1" value="0.22"></td>
        </tr>
        <tr>
            <td>TPA</td>
            <td><input type="number" class="tpa-p" step="0.1" value="0.4"></td>
            <td><input type="number" class="tpa-i" step="0.001" value="0.2"></td>
            <td><input type="number" class="tpa-d" step="0.1" value="0.4"></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <td>Level</td>
            <td><input type="number" class="level-p" step="0.1" value="4"></td>
            <td><input type="number" class="level-i" step="0.001" value="0.04"></td>
            <td><input type="number" class="level-d" step="0.1" value="10"></td>
            <td></td>
            <td>Max&deg;</td>
            <td><input type="number" class="max-deg" step="0.1" value="50"></td>
        </tr>
        <tr>
            <td class="mult-label">1.00x</td>
            <td colspan="6"><input name="multiplier" type="range" step="0.05" min="-1" max="2" value="0" oninput="updateTable('tune1')" class="slider"></td>
        </tr>
    </table>    
</div>
<img src="https://github.com/krunked-fpv/kiss-tuning/blob/main/krunked_tpa.jpg?raw=true" width="660" height="275"/><br>
<img src="https://github.com/krunked-fpv/kiss-tuning/blob/main/flight_performance.jpg?raw=true" width="660" height="175"/><br>
<img src="https://github.com/krunked-fpv/kiss-tuning/blob/main/exp_mode_on.jpg?raw=true" width="660" height="660"/><br>

<script>
// made by the legendary tenten8401 2/9/23
function updateTable(tableName) {
    var table = document.getElementById(tableName);
    var multiplier = parseFloat(table.getElementsByClassName("slider")[0].value);
    const pdRatio = parseFloat(table.getElementsByClassName("pd-ratio")[0].value);
    const maxP = parseFloat(table.getElementsByClassName("max-p")[0].value);
    const maxD = parseFloat(table.getElementsByClassName("max-d")[0].value);
    table.getElementsByClassName("mult-label")[0].innerHTML = parseFloat(multiplier).toFixed(2) + "x";
    
    var newRollP = parseFloat(table.getElementsByClassName("roll-p")[0].dataset.ogvalue) + multiplier;
    if(newRollP > maxP) newRollP = maxP;
    table.getElementsByClassName("roll-p")[0].value = parseFloat(newRollP).toFixed(1);

    var newPitchP = parseFloat(table.getElementsByClassName("pitch-p")[0].dataset.ogvalue) + multiplier;
    if(newPitchP > maxP) newPitchP = maxP;
    table.getElementsByClassName("pitch-p")[0].value = parseFloat(newPitchP).toFixed(1);

    var newRollD = parseFloat(table.getElementsByClassName("roll-d")[0].dataset.ogvalue) + (multiplier * pdRatio);
    if(newRollD > maxD) newRollD = maxD;
    table.getElementsByClassName("roll-d")[0].value = parseFloat(newRollD).toFixed(1);

    var newPitchD = parseFloat(table.getElementsByClassName("pitch-d")[0].dataset.ogvalue) + (multiplier * pdRatio);
    if(newPitchD > maxD) newPitchD = maxD;
    table.getElementsByClassName("pitch-d")[0].value = parseFloat(newPitchD).toFixed(1);
}

// add one of these for each of your tables
updateTable('tune1');
</script>

<style>
    input[type=number]::-webkit-inner-spin-button,
    input[type=number]::-webkit-outer-spin-button {
        opacity: 1;
    }

    .pid-table>table {
        border-collapse: collapse;
        color: white;
    }

    .pid-table {
        background-color: #222222;
        color: white;
        padding: 0.5em;
        font-family: "Titillium Web", sans-serif;
        width: 35em;
        all: initial;
    }

    .pid-table>h4 {
        color: #e09338;
        margin-top: 0;
        margin-bottom: 0.3em;
    }

    .pid-table input {
        width: 6em;
        height: 2em;
    }

    .slider {
        width: 300px;
    }

    .slider-label {
        vertical-align: middle;
        font-size: large;
        padding: 0;
        margin: 0;
    }

    input[type=range] {
        background-color: #222222;
        height: 33px;
        -webkit-appearance: none;
        margin: 10px 0;
        width: 100%;
    }

    input[type=range]:focus {
        outline: none;
    }

    input[type=range]::-webkit-slider-runnable-track {
        width: 100%;
        height: 10px;
        cursor: pointer;
        box-shadow: 1px 1px 1px #000000;
        background: #E09338;
        border-radius: 5px;
        border: 1px solid #000000;
    }

    input[type=range]::-webkit-slider-thumb {
        box-shadow: 1px 1px 1px #000000;
        border: 1px solid #000000;
        height: 25px;
        width: 20px;
        border-radius: 4px;
        background: #FFFFFF;
        cursor: pointer;
        -webkit-appearance: none;
        margin-top: -8.5px;
    }

    input[type=range]:focus::-webkit-slider-runnable-track {
        background: #E09338;
    }

    input[type=range]::-moz-range-track {
        width: 100%;
        height: 10px;
        cursor: pointer;
        box-shadow: 1px 1px 1px #000000;
        background: #E09338;
        border-radius: 5px;
        border: 1px solid #000000;
    }

    input[type=range]::-moz-range-thumb {
        box-shadow: 1px 1px 1px #000000;
        border: 1px solid #000000;
        height: 25px;
        width: 20px;
        border-radius: 4px;
        background: #FFFFFF;
        cursor: pointer;
    }

    input[type=range]::-ms-track {
        width: 100%;
        height: 10px;
        cursor: pointer;
        background: transparent;
        border-color: transparent;
        color: transparent;
    }

    input[type=range]::-ms-fill-lower {
        background: #E09338;
        border: 1px solid #000000;
        border-radius: 10px;
        box-shadow: 1px 1px 1px #000000;
    }

    input[type=range]::-ms-fill-upper {
        background: #E09338;
        border: 1px solid #000000;
        border-radius: 10px;
        box-shadow: 1px 1px 1px #000000;
    }

    input[type=range]::-ms-thumb {
        margin-top: 1px;
        box-shadow: 1px 1px 1px #000000;
        border: 1px solid #000000;
        height: 25px;
        width: 20px;
        border-radius: 4px;
        background: #FFFFFF;
        cursor: pointer;
    }

    input[type=range]:focus::-ms-fill-lower {
        background: #E09338;
    }

    input[type=range]:focus::-ms-fill-upper {
        background: #E09338;
    }
</style>
