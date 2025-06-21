#!/usr/bin/bash

#!/bin/bash

# Extract data using jq and format with awk
jq -r '{name: .name, height: .height, weight: .weight, type: .types[0].type.name}' data.json | \
awk 'BEGIN {FS=":"; OFS=""} \
/"name"/ {name=$2; gsub(/[^a-zA-Z]/, "", name)} \
/"height"/ {height=$2; gsub(/[^0-9]/, "", height); height=height/10} \
/"weight"/ {weight=$2; gsub(/[^0-9]/, "", weight); weight=weight/10} \
/"type"/ {type=$2; gsub(/[^a-zA-Z]/, "", type)} \
END {print name, " is of type ", type, ", weighs ", weight, "kg, and is ", height, "m tall."}' | \
sed 's/\b\w/\U&/g'
