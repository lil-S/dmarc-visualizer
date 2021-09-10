# dmarc-visualizer

Analyse and visualize DMARC results using open-source tools.

* [parsedmarc](https://github.com/domainaware/parsedmarc) for parsing DMARC reports,
* [Elasticsearch](https://www.elastic.co/) to store aggregated data.
* [Grafana](https://grafana.com/) to visualize the aggregated reports.

See the full blog post with instructions at https://debricked.com/blog/2020/05/14/analyse-and-visualize-dmarc-results-using-open-source-tools/.

## Instructions
Step by step instructions for installing dmarc-visualizer by debricked on Windows 10 with WSL 2 and with imap and GeoLite2 Database support.

### Activate WSL 2 and download a Linux Distro
* First of all activate WSL2 in the Windows feature settings and restart your computer
* Go to the Microsoft Store and search for Ubuntu and install it
* More details can be found here: https://docs.microsoft.com/en-us/windows/wsl/install-win10

### Download Docker
Download Docker from here: https://docs.docker.com/desktop/windows/install/

### Enable WSL 2 in Docker
* Open Docker and go to settings 
* Under General click on "Use WSL 2 based engine"
![WSL2Engine](https://user-images.githubusercontent.com/56894465/132823439-4262e2ef-2de0-4ee3-b000-1d4acd61b137.PNG)
* Under Resources/WSL INTEGRATION activate your Linux Distro
![LinuxDistroDocker](https://user-images.githubusercontent.com/56894465/132823716-0aa72d93-08bd-4485-9638-6f64b455c495.PNG)

### Download dmarc-visualizer to your local machine
* Open up your Linux distro and update the package index: `sudo apt update`
* Install git by typing: `sudo apt install git`
* Clone the repository: `git clone https://github.com/debricked/dmarc-visualizer.git`
* Open the repsoitory: `cd dmarc-viszualizer`

### Get the GeoLite2 Database
* Create a user account here: https://www.maxmind.com/en/geolite2/signup
* Sign in with your new user account and generate your license key here: https://www.maxmind.com/en/accounts/605955/license-key?lang=en
* Open your Linux distro and copy this and put your license key after `license_key=`: 
```
sudo curl "https://download.maxmind.com/app/geoip_download?edition_id=GeoLite2-Country&license_key=Your_License_Key_Goes-Here&suffix=tar.gz" -o GeoLite2-Country.tar.gz \
  && tar -xzvf GeoLite2-Country.tar.gz \
  && mkdir -p /var/opt/maxmind/ \
  && mv GeoLite2-Country_*/GeoLite2-Country.mmdb /var/opt/maxmind/GeoLite2-Country.mmdb
```

## Screenshot

![Screenshot of Grafana dashboard](/big_screenshot.png?raw=true)
