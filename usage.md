# CSE489 & CSE589 Test Scripts usage

## Re-compile binary

`./test.sh --compile-binary` It is useful that you made some changes for the python code and you wish to update the binary as well. This command is available in both PA1 and PA2 scripts.

To compile the binary correctly, you need to have `pyinstaller` `staticx` `patchelf` and these have to be installed from `pip3` since this framework does not work with python 2.x and Python foundation dropped 2.x support already.

If the destination system is older than the source system(e.g. Ubuntu 18.04 -> CentOS 7), then the pyInstaller binary will not execute at all.

If you want to compile manually

```bash
pyinstaller -F testTemplate.py
# This step is to ensure the python binary is truly static.
staticx dist/testTemplate testTemplate_bin
```

To install `pyinstaller` `staticx` `patchelf`

```bash
sudo apt install python3-pip
sudo pip3 install pyinstaller staticx patchelf-wrapper
```


## Test script usage for PA1

`./test.sh --generate-json-config` Generate JSON file for all test scripts options for FIRST USE ONLY.

`./test.sh --update` An easier way to update shell scripts and auto test program.

`./test.sh --build` Packing up and prepare to submit

`./test.sh --compile` Build `./assignment1` for this project

`./test.sh --clean` Clean the `.tar` file generated by `Makefile`, and run `make clean` to clean object files

`./test.sh --repeat test_item times` Repeat a test for specified times for diagnosing for grade instabilities 

`./test.sh --test-indv test_item` Test individual test. e.g. `./test.sh --test-indv author` Read [here](https://docs.google.com/document/u/1/d/1Rct0Hv8vmQc6Yub_3SH4ElDkly8rSgNnDKSjrChPjqw/pub) to learn more.

`./test.sh --test-all` **Recommend** Test all tests, and see what's passed and what's failed in addition to the final score.

`./test.sh --repeat-all times` Run `times` times for all test cases to see if grades are stable.

`./test.sh --AIS` Check AI statement locally.


## Test script usage for PA2

`./test.sh --generate-json-config` Generate JSON file for all test scripts options for FIRST USE ONLY.

`./test.sh --update` An easier way to update shell scripts and auto test program.

`./test.sh --compile` Build binaries for this project

`./test.sh --clean` Clean the `.tar` file generated by `Makefile`, and run `make clean` to clean object files

`./test.sh --test-indv test_item` Test individual test. e.g. `./test.sh --test-indv basic ABT` Read [here](https://docs.google.com/document/u/1/d/1z5fHvYeH3_IZYJDBPTk3l2iaKRgJqzpQQUqKYRDiPhw/pub) to learn more.

`./test.sh --test-all` **Recommend** Test all tests, and see what's passed and what's failed in addition to the final score.

`./test.sh --test-basic` Run all basic tests

`./test.sh --test-advanced` Run all advanced tests

`./test.sh --test-sanity` Run all sanity tests

## Test script usage for PA2 report

`./test.sh --run-experiment-1` for generating experiment 1 data

`./test.sh --run-experiment-2` for generating experiment 2 data

`./test.sh --run-all-experiments` for generating all data for experiments

`./test.sh --trim-all-reports` for removing subsequently occured header for all reports

`./test.sh --trim-all-headers` for removing all headers in those generated reports

`./test.sh --add-all-headers` for adding all headers in those generated reports