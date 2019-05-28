# secrawl

SEC-Edgar-Crawler
=============

A simple crawler that parses two classes of corporate filings from EDGAR database: 10Qs & 10Ks.
An easy-to-use starting point to implement different analysis routines including sentiment analysis, textual analysis and other parsing methods.

Installation
------------- 

 You can clone the project or download it as zip.
 ```bash
 $ git clone https://github.com/giuetr/secrawl.git
 $ cd SEC-Edgar
 $ python setup.py install
 ```

Runing
-------
 Check [data.txt][1] to see the format in which name of company's, CIK code date (prior to) and count is given to get the filings of that company.
 
 Now to run it start python shell
   ```bash
  >>> from SECEdgar.crawler import SecCrawler
  >>> secCrawler = SecCrawler()
  >>> secCrawler.filing_10K('AAPL', '0000320193', '20010101', '10')
   ```
 This will download the AAPL company's 10-K filings and the data will be saved in "SEC-Edgar-data" folder which will be created on the run time.


Example 
--------
```python
import time
from SECEdgar.crawler import SecCrawler

def get_filings():
	t1 = time.time()
	
	# create object
	seccrawler = SecCrawler()

	companyCode = 'AAPL'    # company code for apple 
	cik = '0000320193'      # cik code for apple
	date = '20010101'       # date from which filings should be downloaded
	count = '10'            # no of filings
	
	seccrawler.filing_10Q(str(companyCode), str(cik), str(date), str(count))
	seccrawler.filing_10K(str(companyCode), str(cik), str(date), str(count))
	seccrawler.filing_8K(str(companyCode), str(cik), str(date), str(count))
	seccrawler.filing_13F(str(companyCode), str(cik), str(date), str(count))

	t2 = time.time()
	print ("Total Time taken: "),
	print (t2-t1)
	
if __name__ == '__main__':
	get_filings()	
```

Supported Methods
-----------------
Currently this crawler parses 2 classes of filings:
*  10-K
*  10-Q



