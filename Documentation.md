## Datasets

1. The latest **wikidata**: `wget https://dumps.wikimedia.org/wikidatawiki/entities/latest-all.json.bz2`
2. **Popularity** of wikipedia entries: https://dumps.wikimedia.org/other/pageviews/ 
(documentation: https://dumps.wikimedia.org/other/pageviews/readme.html)

Acces the wikipedia pageviews through API: 
https://wikimedia.org/api/rest_v1/#/Pageviews%20data/get_metrics_pageviews_per_article__project___access___agent___article___granularity___start___end_



| Parameter        | values| Description  |
| ------------- |:-------------:| -----|
| project      | en.wikipedia.org | English wikipedia |
| access      | all-access | If you are interested in pageviews regardless of access method, use all-access (desktop, mobile-app, mobile-web) |
| agent      | all-agents | If you are interested in pageviews regardless of agent type, use all-agents. (user, bot, spider) |
| article | Amy_Winehouse  |  The title of any article in the specified project. Any spaces should be replaced with underscores. It also should be URI-encoded,|
| granularity      | monthly | time unit for the response data (daily or monthly) |
| start | 20190101 | The date of the first day to include, in YYYYMMDD or YYYYMMDDHH format |
| end | 20191231 | The date of the last day to include, in YYYYMMDD or YYYYMMDDHH format |

example: `https://wikimedia.org/api/rest_v1/metrics/pageviews/per-article/en.wikipedia.org/all-access/all-agents/Amy_Winehouse/monthly/20190101/20191231`
