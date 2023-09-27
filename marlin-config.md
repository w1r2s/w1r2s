https://3dtoday.ru/blogs/akdzg/custom-firmware-marlin-and-pour-it-into-a-3d-printer -
основные настройки марлина, а также инструкция.
https://www.reddit.com/r/MarlinFirmware/comments/10i2dmd/fysetc_mini_12864_v21_rgb_octopus_v11_marlin_21x/ -
настройка дисплея подгрузить библиотеку U8glib-HAL.h подгрузить
библиотеку Adafruit NeoPixel

настройки Configuration.h:

плата: \#ifndef MOTHERBOARD \#define MOTHERBOARD BOARD_RAMPS_14_EEB
\#endif

дисплей fysetc mini 12864 v2.1: \#define NEOPIXEL_LED \#define SDSUPPORT
\#define FYSETC_MINI_12864_2\_1 \#define NEOPIXEL_LED \#define
NEOPIXEL_TYPE NEO_RGB \#define NEOPIXEL_PIN 4 (кто-то вообще закрывает
это в комменты, разницы не заметил.) \#define NEOPIXEL_PIXELS 30 (кто-то
ставит 3. Разницы не заметил) \#define NEOPIXEL_BRIGHTNESS 255 \#define
LED_CONTROL_MENU (Configuration_adv.h)

концевики: \#define X_MIN_ENDSTOP_INVERTING true \#define
Y_MIN_ENDSTOP_INVERTING true \#define Z_MIN_ENDSTOP_INVERTING true z -
min x - min y - min размер стола: \#define X_BED_SIZE 300 \#define
Y_BED_SIZE 300

позиционирование home: 1 - max, -1 min \#define X_HOME_DIR 1 \#define
Y_HOME_DIR 1 \#define Z_HOME_DIR -1 x,y - home max z - min

endstop settings: //#define USE_XMIN_PLUG //#define USE_YMIN_PLUG
\#define USE_ZMIN_PLUG

\#define USE_XMAX_PLUG \#define USE_YMAX_PLUG

минимальная и максимальная позиция: \#define X_MIN_POS 0 \#define
Y_MIN_POS 0 \#define Z_MIN_POS 0 \#define X_MAX_POS X_BED_SIZE \#define
Y_MAX_POS Y_BED_SIZE \#define Z_MAX_POS 200

скорость перемещения в положение HOME: \#define HOMING_FEEDRATE_MM_M {
(50\*20), (50\*20), (4\*60) } (оставили дефолт)

Настройка ускорения перемещений по осям: \#define
DEFAULT_MAX_ACCELERATION { 1000, 1000, 100, 10000 } \#define
DEFAULT_ACCELERATION 1500

шаги по осям: шаг. двиг - 200 шагов/оборот 16 микрошагов шкив - 20
зубьев шаг резьбы шпильки - 1мм \#define DEFAULT_AXIS_STEPS_PER_UNIT {
(200\*160)/(2.0\*20),(200\*160)/(2.0\*20),(200\*16/1), 500 }
(x,y,z,экструдер). Значение экструдера оставил дефолтным.

Настройки эсктрудера не проводил. \#define ENCODER_PULSES_PER_STEP 2
//количество шагов энкодера за шаг на экране (по улмолчанию 4)
