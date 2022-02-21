!!! warning "Warning"

    This reference is not complete and should not currently be followed


On the previous page, the `.gcsv` format was described. The text-based CSV file has the advantage of being easily formatted and human-read, but the disadvantage of taking up significantly more space that what is required for just the raw data. For instance, a 16-bit or two byte number may take up around 7 bytes due to each decimal being one byte. For this reason, this page describes an alternative format dubbed `.gbin`. This is a binary format and thus significantly more compared than the `.gcsv` format.

## Header
In order to allow for easy identification of the main parameters without decoding the file, the same ASCII header as the `.gcsv` format is used.

```
GYROFLOW GBIN LOG
version,1.1
id,custom_logger_name
orientation,YxZ
note,development_test
fwversion,FIRMWARE_0.1.0
timestamp,1644159993
vendor,potatocam
videofilename,videofilename.mp4
lensprofile,potatocam_mark1_prime_7_5mm_4k
tscale,0.001
gscale,0.00122173047
ascale,0.00048828125
DATA:
t,gx,gy,gz,ax,ay,az
0,39,86,183,-1137,-15689,-2986
1,56,100,202,-1179,-15694,-2887
2,63,108,218,-1247,-15702,-2794
3,71,108,243,-1308,-15675,-2727
4,83,101,268,-1420,-15662,-2661
```

The next is the data:
```
[0xAA][32-bit uint32 time][3x int16][3x int16][3x int16]
```

Behavior of the parser: Start reading, when done, check if the separator is present. 