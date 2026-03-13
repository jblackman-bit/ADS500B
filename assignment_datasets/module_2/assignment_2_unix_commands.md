1.1 awk -F, '{count[$3]++} END {for (p in count) print p "," count[p]}' deaths.csv
1.2.1 awk -F, '/White/&&/Female/ {count[$2 ", " $3]++} END {for (p in count) print p, count[p]}' deaths.csv
1.2.2 awk -F, '/White/&&/Female/ {print}' deaths.csv | sort -t, -k5nr > white_female_deaths.csv
1.2.3 head white_female_deaths.csv
1.3.1 awk -F, '/Black/&&/Male/ {print}' deaths.csv | sort -t, -k5nr | head -3 | cut -d, -f4
1.3.2 awk -F, '/Hispanic/&&/Female/ {print}' deaths.csv | sort -t, -k5nr | tail -5 | cut -d, -f4

2.1 cat population.csv | sort -t, -k4nr | tail -1 | cut -d, -f1
2.2 awk -F, '$3 >10000000 && $4 < 50 {print}' population.csv | cut -d, -f1

3.1 sed 's/"//g' medicines.csv | tail -n +3 | sort -t, -k2nr | tail -1 | cut -d, -f1
3.2 sed 's/"//g' medicines.csv | tail -n +3 | sort -t, -k3nr | head -5 | cut -d, -f1
3.3 sed 's/"//g' medicines.csv | tail -n +3 | awk -F, '{print $0"," $2 - $3}' | sort -t, -k4nr | head -3 | cut -d, -f14