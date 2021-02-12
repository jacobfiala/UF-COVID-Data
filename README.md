# UF-COVID-Data

This data is scraped from three sources:

UF's COVID Dashboard (https://coronavirus.ufhealth.org/screen-test-protect-2/testing-dashboard/)

Alachua County's COVID Dashboard (https://dashboards.alachuacounty.us/COVID19/)

Florida Department of Health repository of COVID19 State Summary Reports (http://ww11.doh.state.fl.us/comm/_partners/covid19_report_archive/cases-monitoring-and-pui-information/state-report/)


## A few notes about each data source:

**UF COVID Dashboard**

I scrape data from two graphs:

The first I refer to as the **Positivity Rate Graph**. 

On the Dashboard it is titled "Number of Daily UF COVID-19 Tests Performed, From Past Month to Present." 
  
  - The numbers on this graph do not change as new data points are added. In other words, the data is stable.
  
  - Although the graph only shows one month at a time, I have been scraping the numbers since the graph was added to the Dashboard on 10/14/20.
  
The second I refer to as the **Case Count Graph**. 

On the Dashboard it is titled "UF Affiliate Cases by Date of Onset of Symptoms, April 2020 - Present." 

  - The totals on this graph are retroactively changed as new data points are added. This effect is most prominent for recent data, i.e., totals for days in roughly the prior two weeks are typically increased daily until they eventually become stable.
  
  - As noted in the title, on this graph, UF organizes cases by the date they *first reported symptoms*, while all other sources reported results by the date that the test was processed. By comparing the data, I was able to determine that, on average, there is a 5 day lag between date of symptom onset and date of test being processed. Therefore, to correct for this when comparing this data to other sources, I shift the totals down 5 days. For example, the first day I have data for is 3/18, but this total is shifted down to 3/23.
  
  - Additionally, as the Dashboard notes, these totals reflect testing done on campus and through external labs. UF is notified by FL DOH when a UF affiliate tests positive in the community, so they can do contract tracing on these individuals.
  
  - Finally, because this graph only lists "UF Affiliate Cases", it does not provide a count of negative tests. This is understandable, since the UF affiliates that tested positive at a non-uf, community testing source are included. So, to report negatives as well, they would also have to be notified by community providers when a UF affiliate tests *negative*.
  
**Alachua County Dashboard**

Again, I scrape data from two graphs. They are both under the "Testing" Section. The first is titled "Positive Tests per Day" and the second is titled "Negative Tests per Day."

  - Although they do not state this on the Dashboard, the positives and negatives recorded here refer to people who were *tested in Alachua County* **and** who *are Florida residents*. Obviously, this may neglect a substantial amount of UF's students.
 
  - Data is mostly stable. However, every Monday, the totals from the prior week are changed minorly. So far, this usually consists of a few of the negatives for each day in the prior week being changed to positives.

**Florida Department of Health COVID19 State Report repository**

I scrape data from UF Health's 3 main laboratories in the section of the report titled "COVID-19: testing by laboratory"
 
  - These 3 main labs (UF Health Medical Lab, UF Health Shands Hospital, UF Health Jacksonville) began to be included in these reports on 11/5/20 (summarizing the data for 11/4/20). So this data begins at this point.
  
  - Daily totals are calculated by subtracting the cumulative total on one day from the cumulative total on the previous day (i.e., the amount of test results added to the running total on that day).
  
  - If you comb through the reports, you may notice there are a few other UF Health Labs listed besides the three that I am scraping data from. I didn't include them because they have conducted a negligible amount of tests since the pandemic began. For example: UF HEALTH NORTH JACKSONVILLE only records 23 and the rest record less than 10 each.
  
  - A major advantage of this data, as noted in the reports, is that it includes the results of both Florida and non-Florida residents, meaning that it captures UF Affiliates who are not legal residents of Florida.
  
  - It's worth noting that UF Health Laboratories are likely also processing the tests of community members who are not UF Affiliates. However, it is worth noting that it has been previously reported that UF Student and Faculty tests are processed at UF Health Medical Lab (https://www.firstcoastnews.com/article/entertainment/television/programs/gmj/a-behind-the-scenes-look-at-uf-health-covid-19-testing/77-bb0016fa-75d2-41bf-b7b6-9241cc2e0da7). So it might be safe to presume that the majority of tests processed by this lab belong to UF Affiliates.
