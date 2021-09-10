# olaDMXctl
Command-line tool for controlling individual dmx channels with olad





## installation
### php and curl
This tool is coded in php and uses curl for http-requests so you need to have that installed

```bash
sudo apt update
sudo apt install php curl
```


### download
Download the script from github
```bash
wget https://github.com/DrMaxNix/oladmxctl/releases/download/v1.0.2/oladmxctl
```

Make it executable
```bash
chmod +x oladmxctl
```


### move into /usr/bin (optional)
You can skip this step. This will only make it so you can call the script from everywhere using `oladmxctl`. If you skip this step you will have to use `./oladmxctl` or `/path/to/oladmxctl` to run the script.

```bash
sudo mv oladmxctl /usr/bin
```





## usage
```
oladmxctl --universe <universe> [--write <json>] [--read <json>]

-s --silent           No error/warning/info output

-u --universe         Universe number to control
-w --write            JSON-encoded string with channel-value pairs to write
-r --read             JSON-encoded string with channels to read from and output
                      to stdout as JSON-encoded string with channel-value pairs
-f --force-rewrite    Force write request to olad even if no data has changed

-1 --ch-offset        First channel has number 1

-a --address          Address of the olad instance (default 127.0.0.1)
-p --port             Port of the olad instance (default 9090)
-3 --ssl              Use https instead of http

-h --help             Show this help and exit
-v --version          Print version and exit
```
  




## examples
### Set channel 13 and 14 to 255 in universe 1
```bash
oladmxctl --universe 1 --write '{"13":255, "14":255}'
```



### Read channels 13 and 14 in universe 1
```bash
oladmxctl --universe 1 --read '[13, 14]'
```
Returns `{"13":255, "14":255}`
