# test_ws
Zigbee2MQTT version: 1.25.2  
Coordinator type: zStack3x0  
Coordinator revision: 20220524  
Frontend version: 0.6.103  

1. Отредактировать файл `/zigbee2mqtt/node_modules/zigbee-herdsman-converters/devices/jethome.js` (https://github.com/Koenkk/zigbee-herdsman-converters/blob/master/devices/jethome.js)

    * В строку 6 добавить: `const ota = require('../lib/ota');`
    * В строку 30 добавить: `ota: ota.zigbeeOTA,`

2. Перезапустить zigbee2mqtt

3. Открыть WEB-интерфейс zigbee2mqtt. Перейти в раздел: `Settings/OTA updates/` 
  В поле `OTA index override file name` указать: `https://github.com/0x3EC/test_ws/raw/master/jh_index.json`  
  Нажать ***'Submit'***.

4. Перейти в раздел `OTA`. Нажать кнопку ***'Check for new update'*** напротив WS7. На WS7 нажать кнопку переключения режимов. Подождать появления кнопки ***'Update device firmware'***. Нажать на нее. 

5. На WS7 с периодом ~2 сек нажать 3-4 раза на кнопку переключения режимов. Начнется процесс обновления. Время обновления около 80 минут. 






# zigbee-OTA
A collection of Zigbee OTA files, see `index.json` for an overview of all available firmware files.

## Adding new and updating existing OTA files
1. Go to this directory
2. Execute `node scripts/add.js PATH_TO_OTA_FILE_OR_URL`, e.g.:
    - `node scripts/add.js ~/Downloads/WhiteLamp-Atmel-Target_0105_5.130.1.30000_0012.sbl-ota`
    - `node scripts/add.js http://fds.dc1.philips.com/firmware/ZGB_100B_010D/1107323831/Sensor-ATmega_6.1.1.27575_0012.sbl-ota`
3. Create a PR

## Updating all existing OTA entries (if add.js has been changed)
1. Go to this directory
2. Execute `node scripts/updateall.js`
3. Create a PR
