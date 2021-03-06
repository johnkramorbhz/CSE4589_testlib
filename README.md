# CSE489 & CSE589 Auto Tester Framework

PROVIDED AS IS WITHOUT WARRANTY OR SERVICE. You may fork this project and continue on your own. However, I will not push any more changes unless it is a bugfix. Only work with these projects in these links. [Link1](https://docs.google.com/document/u/1/d/135usaNDMnJ5pEDG-UbspZameDPmOH0DmXLrMVrLVJ88/pub) [Link2](https://docs.google.com/document/u/1/d/19I8-TrLNcfaCGX1L-KSx5xFYEoiFAN3F9o_jQlOgsFM/pub)

### [Click here for usage](https://github.com/johnkramorbhz/CSE4589_testlib/blob/main/usage.md)

## Please Note

This repo was moved from Scripts repo, once the move is complete the readme file on the old one will reference here instead.

## Installation

Why here? It will take care of populating PA1 & PA2 for you. In addition, it will also prepare test scripts for both PA1 and PA2. After installation, you will need to add the following info in these scripts.

After installation, run `./test.sh --generate-json-config` in either one of the CSE489 or CSE589 assignment folder. Then it will produce a json profile called `CSE4589.config.json` in the `framework` folder, which contains following options.

You will need to fill out `FullName`, `UBITname`, `Person_Number`, and `semester`. You can keep other values default as those are script options.
```json
{
    "FullName": "replace_with_your_full_name",
    "Person_Number": 12345678,
    "UBITname": "replace_with_your_ubitname_here",
    "Upgrade_Path": "main",
    "debug": false,
    "format_level": 2,
    "gradMode": false,
    "quiet": false,
    "semester": "Fall_9999",
    "suppressHeader": false,
    "timeout": 190
}
```

If you do not want to use `python3` (A backup solution)

`wget https://github.com/johnkramorbhz/Scripts/raw/main/unit_tests/CSE489/testTemplate_bin && chmod u+x testTemplate_bin && ./testTemplate_bin install`

If you want to use `python3` **Preferred**

`wget https://github.com/johnkramorbhz/Scripts/raw/main/unit_tests/CSE489/testTemplate.py && python3 testTemplate.py install`

After installation, the directory structure looks like this

```
.
├── cse489589_assignment1
├── cse489589_assignment2
└── framework

3 directories
```

It requires `python3` on CentOS 7 and later(e.g. Ubuntu 18.04, Ubuntu 20.04, and later). If it does not work for whatever reason or you prefer one of the modes, find these lines in the `test.sh`. **If you run `--update` function, you WILL need to set these options again as updating process will overwrite all settings embedded in shell code!**

```bash
#use_binary="false" #Uncomment this line to force binary
#use_binary="force_script" #Uncomment this line to force Python3 interpreter
```

## Update

**If you have the test script below 2.4.x, use this method because the shell script did not enable `--update` flag yet.**

Both script version and binary version in this repo supports update from themselves. AFTER go to `framework` directory, use the command below

Script version: `python3 testTemplate.py update`

Binary version: `./testTemplate_bin update`

## High-level overview

Under `framework/report`, there are reports having name of `PAX_Date_Time`, where date is formatted `YYYY-MM-DD` and time is `HH.MM.SS`

`testTemplate.py` is the backend of the `./test.sh` in each Programming Assignment folder

It is also available in the binary form, which is `testTemplate_bin`. You need `pyInstaller` & `staticx` to create a static binary that works on any Linux machines/servers. [Compile Guide](https://github.com/johnkramorbhz/Scripts/blob/main/unit_tests/CSE489/usage.md#re-compile-binary)

## Interpret `.csv` files that are used in the readCSV() function

For PA1, it is 

`author,author,0` means `friendly name, shell command, common grade`

For PA2, some files will have 4 columns instead of 3.

If a CSV file have 4 columns, it means `friendly name,shell command,undergrad grade,grad grade`

For PA2 experiments, it is divided by PA2 documentation. LOOK CAREFULLY for what it asks. Even though I don't think he will change anything.

## Interpret `experiments.csv` files

"loss","window","binary_name"

e.g.

`0.1,10,sr`

## High Level Design of This Framework

The `test.sh` in each Programming Assignment directory is a high level abstraction of the python script, because python scripts have many differnt arguments depending on its tasks.

The python script is unified instead of dividing it into each individual PA test script, because the enhancement will benefit both PAs.

The main goal of this script is to save time for debugging, and have some estimation of final grade.
