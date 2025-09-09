# Assignment 01 – Subdomain Enumeration using Subfinder, Assetfinder, and Alterx

## ✅ Objective
The objective of this assignment is to collect subdomains of any two targets using three popular enumeration tools/scripts:
1. **subfinder**
2. **assetfinder**
3. **alterx**

This helps in gathering information about the target’s attack surface by identifying active subdomains.

---

## 🎯 Targets
- **Target 1**: https://virustotal.com
- **Target 2**: https://securitytrails.com

---

## 🛠 Tools Used

| Tool       | Description |
|------------|--------------|
| subfinder  | Fast subdomain enumeration tool that discovers valid subdomains using passive sources. |
| assetfinder | Finds domains and subdomains using publicly available sources. |
| alterx     | Aggregates and correlates subdomain data from multiple sources. |
| dnsx | Fast and Flexible DNS resolution tool that helps verify, probe, and gather DNS information for domains and subdomains

---

## ✅ Methodology

### Subfinder
1. Installed subfinder using Go.
   ```bash
   go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
   ```  
2. Ran the subdomain scan for both targets using the following command:
   ```bash
   subfinder -d target1.com > subfinder-output1.txt
   subfinder -d target2.com > subfinder-output2.txt
   ```

### Assetfinder
1. Installed assetfinder using Go.
   ```bash
   go install github.com/tomnomnom/assetfinder@latest
   ```
2. Ran assetfinder scan for both targets:
   ```bash
   assetfinder target1.com > assetfinder-output1.txt
   assetfinder target2.com > assetfinder-output2.txt
   ```

### Alterx
1. Installed Alterx using Go.
   ```bash
   go install github.com/projectdiscovery/alterx/cmd/alterx@latest
   ```
2. Ran Alterx to find permutations of subdomains gathered using Subfinder and Assetfinder
   ```bash
   cat subfinder-output1.txt assetfinder-output1.txt | alterx -p '{{sub}}-{{word}}.{{suffix}}' -o alterx-permutations-output1.txt
   cat subfinder-output2.txt assetfinder-output2.txt | alterx -p '{{sub}}-{{word}}.{{suffix}}' -o alterx-permutations-output2.txt
   ```

### dnsx
1. Installed dnsx using Go.
   ```bash
   go install -v github.com/projectdiscovery/dnsx/cmd/dnsx@latest
   ```
2. used dnsx to verify the permutations compiled using alterx as active subdomains
   ```bash
   cat alterx-permutations-output1.txt | dnsx -o active-subdomain1.txt
   cat alterx-permutations-output2.txt | dnsx -o active-subdomain2.txt
   ```
   
---

## 📊 Results

### Target 1 : https://virustotal.com

1. Subfinder -
2. Assetfinder -
3. Alterx - 
4. Active Subdomains -

### Target 2 : https://securitytrails.com

1. Subfinder - 
2. Assetfinder - 
3. Alterx - 
4. Active Subdomains - 
