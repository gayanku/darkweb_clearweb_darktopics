# darkweb_clearweb_darktopics : Darkweb forums and clear web forums on darkweb topics
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository contains 7 darkweb market forum datasets, with usernames obfuscated.
The original data is from [Ladegaard, I. (2020). Open secrecy: How police crackdowns and creative problem-solving brought illegal markets out of the shadows](https://academic.oup.com/sf/article/99/2/532/5805358?login=false)

### The forums are in 2 files
- forum_data_part1.csv.zip
https://drive.google.com/file/d/1RAOwpvjZSYzpgui5h1kpEER-vZnZ-rvq/view?usp=sharing

- forum_data_part2.csv.zip
https://drive.google.com/file/d/1sPmLmiLwOJVFCgBetiAJYCospsz7JVI_/view?usp=sharing

This work uses the following 5 real world darkweb forums:
1. **Silk Road 1 Forum**: Discussion forum for users of the original crypto market, Silk Road (also referred to as Silk Road 1). The market and this forum were shut down by the FBI in October 2013. Html files for this dataset were downloaded from the Dark Net Market archives, 2011-2015 by \cite{dnmArchives}.
2. *8Silk Road 2 Forum**: Discussion forum for users of the cryptomarket Silk Road 2. The market and this forum were shut down by the FBI in November 2014. Some of the HTML files for this dataset were downloaded directly from the forum, others from the Dark Net Market archives, 2011-2015 by \cite{dnmArchives}.
3. **Agora Forum**: Discussion forum for users of the cryptomarket Agora. The market and the forum were shut down by its operator. Users were given advance notice. Some of the HTML files for this dataset were downloaded directly from the forum, others from the Dark Net Market archives, 2011-2015 by \cite{dnmArchives}.
4. **Black Market Reloaded Forum**: Discussion forum for users of the cryptomarket Black Market Reloaded. The market and the forum were shut down by its operator. All users were given advance notice. Html files for this dataset were downloaded from the Dark Net Market archives, 2011-2015 by \cite{dnmArchives}.
5. **Evolution Forum**: Discussion forum for users of the cryptomarket Evolution. The market and this forum were shut down by its operator, without notice, in a so-called 'exit scam.' Some of the HTML files for this dataset were downloaded directly from the forum, others from the Dark Net Market archives, 2011-2015 by \cite{dnmArchives}.

and 2 clearweb Reddit forums that discuss topics related to darkweb
6. **Reddit Darknet Markets*: Reddit page for users of all cryptomarkets (or darknet markets). The subreddit was banned in 2018. All data were collected directly from reddit.com/r/DarkNetMarkets/ in late 2017.
7. **Reddit Silk Road (1\&2)*: Reddit page for users of the original cryptomarket, Silk Road, and Silk Road 2. All data were collected directly from reddit.com/r/SilkRoad/ in late 2017.

### The market data is in 1 file

- market_data_obfuscated.csv.zip
https://drive.google.com/file/d/1t2sSsCo9LD1yfcQzkxU4ABUVrZvGYxB6/view?usp=sharing

1. **Silk Road 2**: was launched in November 2013, about one month after its predecessor was shut down by the FBI. Data were collected over 20 consecutive days, until it too was shut down in another law enforcement operation in November 2014.
2. **Agora**: launched in 2013 and shut down voluntary in August 2015, after notifying its users. Data from Agora were collected on a daily basis from early November 2014 until its final days in 2015.
3. **Evolution**: opened in early 2014 and shut down voluntarily in the spring of 2015, with no notice to its users, in a so-called exit-scam. Data from Evolution were collected on a daily basis from early November 2014 until it shut down in March the following year.

## Preprocessed forum content

The bellow table shows the preprocessed content with unparsable dates cleaned up, taking the actual forum active dates ( start date and end date) in to account

| Forum                         | Original posts | After clean-up | Filter from | date Filter to | Forum from |   Forum to |
|-------------------------------|---------------:|---------------:|------------:|---------------:|-----------:|-----------:|
| Agora                         |        1047499 |         976447 |   3/12/2013 |     26/08/2015 |  3/12/2013 | 26/08/2015 |
| Black Market Reloaded*        |          83269 |          81413 |  30/06/2011 |     2/12/2113* | 30/06/2011 |   2/12/213 |
| Evolution                     |         432024 |         383629 |  14/01/2014 |     14/03/2015 | 14/01/2014 | 14/03/2015 |
| Silk Road 1                   |        1215091 |        1145989 |  31/01/2011 |      2/10/2013 | 31/01/2011 |  2/10/2013 |
| Silk Road 2                   |         804655 |         770078 |   6/11/2013 |      5/11/2014 |  6/11/2013 |  5/11/2014 |
| Reddit Darknet Markets        |        1105626 |        1105330 |   1/01/2013 |     22/03/2018 |  1/01/2013 | 22/03/2018 |
| Reddit Silk Road              |         122394 |         122341 |   1/01/1900 |      1/01/2100 |  1/01/1900 |            |

**preprecessing invloved** : filtering out all posts that could not create valid timestamps after attempting to recover much posts as possible. For example, we recovered "At 10.30" and "9.45 pm" by removing the offending text snippets "At" and "pm". We dropped "Yesterday", "Today" posts as we do not have information of the actual time they were scraped, or the time zone. We also dropped other text not directly convertible as a valid time. In cases where the date was present with no time value, we still attempted to reconstruct the datetime as date:00:00:00. In the obtained data times, we still found incorrect values such as a date "2061-06-01 00:00:00" for Silkroad 1. For this reason, we filtered the datetimes for the active period of each darkweb forum, based on the pragmatic assumption that posts can only originate within the lifespan of the forum.

To download, as a pandas dataframe, please use 
- Clearnedup_ALL_7.csv.zip
https://drive.google.com/file/d/1U7UV7RhE7gDSZC5xe7XaUifetwlZlu2I/view?usp=sharing

```
import pandas as pd
forum_df = pd.read_csv('Clearnedup_ALL_7.csv', parse_dates=['datetime']) 
```
