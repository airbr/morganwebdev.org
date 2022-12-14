---
title: "Performance"
date: 2022-12-12T8:00:00-08:00
draft: false
tags: 
   - Performance
   - Web Performance
   - Core Web Vitals
   - Lighthouse
   - SiteSpeed
   - YellowLabTools
   - Bash
   - Unix
   - Reporting
---

# Web Performance is good (and can be fun)


An example Lighthouse score:

![](/lighthouse.png)

I have a growing interest in web performance. I get joy out of using web performance tools and hopefully getting a good score on the pages I work on. It is a little like working to get a gold star and then see your website perform out in the big world!

Performance matters on a big scale and small scale - Core Web Vitals is a ranking factor for Google SEO. Theres a whole genre of statistics that basically tell you "People lose interest fast when your site is slow".

# Initial tools

There are a number of web performance tools but there are three so far I have experimented with:

* [Lighthouse](https://github.com/GoogleChrome/lighthouse) - Embedded into the Chrome Browser, able to be run CLI or in Node programmatically
* [SiteSpeed.io](https://www.sitespeed.io/) - Open Source tool, vibrant, comes with a coach to help you improve your website!
* [Yellow Lab Tools](https://yellowlab.tools/) - Smaller OSS tool, another tool in the belt

I see a benefit in running multiple kinds of tests and comparing the results against each other if anything is an issue.

# My project idea: '[bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell))' them togethor 

### [My small project on GitHub, a bash program that collects the results of performance tests from lighthouse, sitespeed and yellowlabtools: https://github.com/airbr/performance](https://github.com/airbr/performance)


You can see the changing status of the project at that repository, below is a section at the current time which may be less likely to change:

```
    curl=$(curl -Is --max-time 15 "$line");
    res=$?
    if test "$res" != "0"; then
        printf "the curl command failed for %s with: %s \n" "$line" "$res" | tee -a "$filename";
        
    else
        printf "\n";
        printf "\n";
        printf "The curl command was successful for %s. It exited with a status code of:" "$line" | tee -a "$filename";
        printf "%s" "$curl" | head -n 1 | tee -a "$filename";
        printf "\n";
        printf "\n";
        printf "COMMENCING ADDITIONAL TESTS:";
        printf "\n";
        printf "\n";

        if [[ -n $lflag ]]; then
            lighthouse "$line" --output json --output-path ../output/$date/$domain-$tld-lighthouse-result.json &
        else
            echo "NO Lighthouse test, try -l next time";
        fi

        if [[ -n $yflag ]]; then
            yellowlabtools "$line" > ../output/$date/$domain-$tld-yellow-lab-result.json &
        else
            echo "NO YellowLabTools test, try -y next time";
        fi

        if [[ -n $sflag ]]; then
            sitespeed.io "$line" --summary-detail --outputFolder ../output/$date/$domain-$tld-sitespeed-result/ &
        else
            echo "NO Sitespeed test, try -s next time";
        fi

    fi
```

Currently my process is to run a curl command to determine that the website is up and available to the network roughly. Then I proceed to check the presence of flags to control flow running the rest of the programs.


# Future Development

The next thing is the big question. As you can see on the [files on Github](https://github.com/airbr/performance/blob/main/src/battery.sh), Ive started working with a way to copy the test results to a file in the form of a summary or write up a report from the findings of the tests.

What I am really interested in doing is running tests where the output is put in [charts.js](https://www.chartjs.org/) or something similar to create a performance dashboard of websites tested.

I will be working on this project. But for now, enjoy some web performance in the links shared above!