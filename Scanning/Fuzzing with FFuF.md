# Fuzzing with FFuF

## Install latest version

```
go get github.com/ffuf/ffuf
```

## Update latest version

```
go get -u github.com/ffuf/ffuf
```

## Run latest version

```
~/go/bin/ffuf
```

## Run first scan

```
ffuf -u https://example.com/FUZZ/ -w ./wordlist
```

## Run recursively

```
ffuf -u https://example.com/FUZZ -w ./wordlist -recursion -recursion-depth 1
```

## Specify file extension

```
ffuf -u https://example.com/FUZZ -w ./wordlist -e .bak
```

## Custom fuzz word

```
ffuf -u https://example.com/W1 -w ./wordlist:W1 -e .bak
```

> This method does not include recursion

## Silent mode + tee

```
ffuf -u https://example.com/FUZZ -w ./wordlist -s | tee ./outfile.txt
```

## Generating a report

```
ffuf -u https://example.com/FUZZ -w ./wordlist -of html -o ./report
```

## Authentication: Cookies

```
ffuf -u https://example.com/FUZZ -w ./wordlist -b "NAME1=VALUE1; NAME2=VALUE2"
```

## Authentication: Headers

```
ffuf -u https://example.com/FUZZ -w ./wordlist -H "NAME1=VALUE1; NAME2=VALUE2"
```

## Multiple domains

```
ffuf -u https://W2.com/W1 -w ./wordlist:W1 -w ./domains:W2
```

## Using a request file

```
ffuf -request /tmp/request -w ./wordlist
```

> The request file should contain the FUZZ keyword!

## Using pitchfork mode

> Default mode in ffuf is cluster bomb

```
ffuf -request -w ./users:W1 ./passwords:W2 -mode pitchfork
```

## Rate limiting

```
ffuf -request -w ./wordlist -rate 100
```

## Filters

>Removes the req/res which match the filter. Use this if you know what you want to remove.

```
ffuf -request -w ./wordlist -fr "not found"
```

## Matchers

> Keeps the req/res which match the matcher. Use this if you know what you want to keep.

```
ffuf -request -w ./wordlist -mc 201
```

## Fuzzing POST data

```
ffuf -u https://example.com/login -w ./wordlist.txt -X "POST" -d "email=test@mail.com&password=FUZZ"
```

## Fuzzing POST parameters

```
ffuf -u https://example.com/update -w ./wordlist.txt -X "PUT" -d "FUZZ=massassignment"
```

## Fuzzing JSON POST data

```
ffuf -u https://example.com/update -w ./wordlist.txt -X "PUT" -H "Content-Type: application/json" -d "{'FUZZ': 'test'}"
```

## Replay proxy \(local or remote\)

```
ffuf -request -w ./wordlist -replay-proxy http://127.0.0.1:8080
```

## More to look up

- Stop on spurious requests
- Request throttling and delay
- Automatically calibrate filters
- Custom automatic calibration filtering