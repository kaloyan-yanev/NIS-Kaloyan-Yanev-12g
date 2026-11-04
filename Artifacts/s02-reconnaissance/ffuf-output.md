# FFUF Report

  Command line : `ffuf -u http://67.67.67.3:8080/FUZZ -w /usr/share/SecLists/Discovery/Web-Content/common.txt -fc 404 -o ffuf_output.md -of md`
  Time: 2026-11-04T16:04:51-05:00

  | FUZZ | URL | Redirectlocation | Position | Status Code | Content Length | Content Words | Content Lines | Content Type | Duration | ResultFile | ScraperData | Ffufhash
  | :- | :-- | :--------------- | :---- | :------- | :---------- | :------------- | :------------ | :--------- | :----------- | :------------ | :-------- |
  | docs | http://67.67.67.3:8080/docs | /docs/ | 1533 | 302 | 0 | 1 | 1 |  | 4.253012ms |  |  | 85a705fd
  | examples | http://67.67.67.3:8080/examples | /examples/ | 1721 | 302 | 0 | 1 | 1 |  | 4.477653ms |  |  | 85a706b9
  | favicon.ico | http://67.67.67.3:8080/favicon.ico |  | 1773 | 200 | 21630 | 19 | 22 | image/x-icon | 1.967196ms |  |  | 85a706ed
  | host-manager | http://67.67.67.3:8080/host-manager | /host-manager/ | 2112 | 302 | 0 | 1 | 1 |  | 4.315809ms |  |  | 85a70840
  | manager | http://67.67.67.3:8080/manager | /manager/ | 2613 | 302 | 0 | 1 | 1 |  | 3.626805ms |  |  | 85a70a35
  