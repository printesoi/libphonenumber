libphonenumber
==============

golang port of Google's libphonenumber

This is a clone of the [libphonenumber](http:///github.com/ttacon/libphonenumber)
repository with some minor adjustments:

- Go module support
- Remove the github.com/ttacon/builder dependency by bundling it as subfolder
- Update metadata

[![forthebadge](http://forthebadge.com/images/badges/no-ragrets.svg)](http://forthebadge.com)

[![Build Status](https://github.com/printesoi/libphonenumber/actions/workflows/go.yaml/badge.svg)](https://github.com/printesoi/libphonenumber/actions)
[![GoDoc](https://godoc.org/github.com/ttacon/libphonenumber?status.png)](https://godoc.org/github.com/ttacon/libphonenumber)

Status
======

This library is fully stable and is used in production by several companies.

Examples
========

Super simple to use.

### To get a phone number

```go
num, err := libphonenumber.Parse("6502530000", "US")
```

### To format a number

```go
// num is a *libphonenumber.PhoneNumber
formattedNum := libphonenumber.Format(num, libphonenumber.NATIONAL)
```

### To get the area code of a number
```go
// Parse the number.
num, err := libphonenumber.Parse("1234567890", "US")
if err != nil {
        // Handle error appropriately.
}

// Get the cleaned number and the length of the area code.
natSigNumber := libphonenumber.GetNationalSignificantNumber(num)
geoCodeLength := libphonenumber.GetLengthOfGeographicalAreaCode(num)

// Extract the area code.
areaCode := ""
if geoCodeLength > 0 {
        areaCode = natSigNumber[0:geoCodeLength]
}
fmt.Println(areaCode)
```
