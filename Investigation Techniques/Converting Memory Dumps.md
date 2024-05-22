# Converting Memory Dumps

There are a couple types of memory dump types: raw, crash dump, hibernation dump, vm dump
Each one of them, except the raw dump format, has its own headers and ways of organising the data contained inside the memory dump. Therefore sometimes it's better to just convert them to the basic raw format, to avoid delays and complications
while conducting analysis. 

## Conversion with Volatility

The conversion of memory dumps to the raw format can be done with help of volatility:

```
python vol.py -f dump.mem --profile=machine_profile imagecopy -O dump.raw
```

After conversion, the output dump will be in the raw format, ready for analysis.
Volatility also provides one more interesting conversion option. When we have a
raw memory dump, we can convert it to a crashdump to analyse it in WinDBG:

```
python vol.py -f dump.raw --profile=machine_profile raw2dmp -O dump.mem
```
