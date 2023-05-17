<h1 align="center">ZIP Domains <a href="https://twitter.com/intent/tweet?text=Newly%20registered%20.zip%20domains%0Ahttps%3A%2F%2Fgithub.com%2Ftrickest%2Fzip"><img src="https://img.shields.io/badge/Tweet--lightgrey?logo=twitter&style=social" alt="Tweet" height="20"/></a></h1>
<h3 align="center">Newly registered .zip domains</h3>

Our mission with this project is to provide an update data on newly registered [.zip domains.](https://domains.google/tld/zip/)

As we saw, community is worried on [potential attack vectors](https://medium.com/@bobbyrsec/the-dangers-of-googles-zip-tld-5e1e675e59a5) that could be used.

# DNS Data

This repository contains DNS data organized into CSV files. Each CSV file represents a collection of DNS records and includes the following properties for each record:

- Host: The hostname or domain associated with the record.
- A: The IP address corresponding to the host.
- SOA: Start of Authority record for the domain.
- NS: Name Servers responsible for the domain.
- Status Code: The DNS response code for the query.
- CDN: Indicates whether the record is served through a Content Delivery Network (CDN).
- CDN Name: The name of the CDN used, if applicable.

## The data

Here's an example of how the data is structured in the CSV files:


| Filename | Hosts                                          | SOA                            | NS                                                                 | Status Code | A                                                              | CDN | CDN Name | AAAA                          | MX | TXT | CNAME | CAA | PTR | Has Internal IPs | Internal IPs                                    |
|----------|------------------------------------------------|--------------------------------|--------------------------------------------------------------------|-------------|----------------------------------------------------------------|-----|----------|-------------------------------|----|-----|-------|-----|-----|------------------|------------------------------------------------|
| backup.zip  | ns1.name.com, hostmaster.nsone.net              | ns4fmw.name.com, ns2dky.name.com, ns1bdg.name.com, ns3dkz.name.com | NOERROR                                                            |             | 91.195.240.94, 163.114.216.17, 163.114.216.49, 163.114.217.17, 163.114.217.49 |     |          | 2a00:edc0:107::49              |    |     |       |     |     |                  |                                                  |
## How It Works

![Trickest Workflow - SSL](images/zip.png "Trickest Workflow - zip")
### TB; DZ (Too big; didn't zoom):

1. Download [479k English words](https://github.com/dwyl/english-words) to be used as wordlist
2. Download top [10 Million Websites](https://www.domcop.com/top-10-million-websites). Use a bash script to delete .tlds and get only the company names
3. Use bash to create permutations

```
while read -r word; do
    while read -r line; do
        echo "${word}${line}"
        echo "${line}${word}"
        echo "${line}-${word}"
        echo "${word}-${line}"
    done < domains.txt
done < words.txt
```

4. Generate batched pattern to be able to execute the workflow in parallel on 50 machines
5. Use dnsx to resolve and get JSON data
6. Merge the data from parallel executions
7. Create CSV `zip-domains.csv` 
8. Push to repository

## Contribution
All contributions/ideas/suggestions are welcome! Feel free to create a new ticket via [GitHub issues](https://github.com/trickest/cloud/issues), tweet at us [@trick3st](https://twitter.com/trick3st), or join the conversation on [Discord](https://discord.gg/7HZmFYTGcQ).

## Build your own workflows
We believe in the value of tinkering; cookie-cutter solutions rarely cut it. Sign up to [Trickest](https://trickest.com) to customize this workflow to your use case, get access to many more workflows, or build your own workflows from scratch!

[<img src="images/banner.png" />](https://trickest-access.paperform.co/)