---
layout: page
title: Fetch
---

# Content Fetching
The app has several tools for content fetching, from social media and other sources.

## Twitter
The app can be used to fetch tweets through the <a href="https://developer.twitter.com/en/docs" target="_blank">**Twitter API**</a>.

> #### API Key
> Please refer to the Twitter documentation in order to obtain the API Keys (that are necessary to use the Twitter fetcher). Please also be aware of the **API limits**, which might change depending on Twitter policy.

> #### Search Query
- The **search query** can be specified by using Twitter <a href="https://developer.twitter.com/en/docs/tweets/rules-and-filtering/overview/standard-operators" target="_blank">**standard operators**</a>, an example is `(happy AND hour) OR #freedrinks`. Please do not specify the language in this query. The corresponding search results can be visualized on <a href="https://search.twitter.com" target="_blank">**search.twitter.com**</a> (this is a recommended step before starting the fetcher).
- **Language** is used to specify the language of tweets.
- The **maximum number of tweets** has to be specified to avoid exceeding the API limits.
- **Wait if rate limit reached** tells the system to wait and continue the query after sufficient time has passed and API limits are restored. **Please avoid using this in combination with a high number set for the maximum number of tweets**.

> #### Run
> Starts the fetcher and collects the tweets that match the search query. Tweets can be downloaded and subsequently uploaded in the app for the analysis. In case of errors, the fetcher can also be **stopped**.
>
> #### Output
>
> A CSV file where the comma is used as separator.

## Telpress
Researchers and companies can request access to this news portal directly contacting <a href="http://www.telpress.com/" target="_blank">**Telpress International**</a>. The company collects online and offline news from all over the world, with a special focus on Italy. Files are downloaded in a format ready for the SBS BI app.

## Event Registry
Event Registry is a system that allows real-time collection of content published by global news outlets. The SBS BI app uses the Event Registry APIs to allow the search and dowload of global news. The main parameters are described here:

> #### API Key
> Is the API Key available once registered on <a href="https://eventregistry.org/" target="_blank">**eventregistry.org**</a>. Please be aware of (free) API limitations, which might change depending on Event Registry policy.

> #### Search Query
- The **query operator** defines the logical operator used for the words listed in the search query field .`AND ` means that ALL the words listed in the second field have to be in the articles. `OR` means that at least one of the words listed in the second field have to be in the articles. 

- **Article sources** is used to select one or more data sources.

- The second field is used to specify the **search query**. Please insert a list of words separated by commas (without quotes unless containing whitespaces). E.g.: "hey you",word1,word2.

- The third field is used to **exclude articles** that contain ANY of the listed words.

- **Start and end time** indicate the period of data collection. Free API might have limitations and not allow the collection of news older than one month.

- **Language** is used to specify the article language.

- You can choose to **concatenate tile and body**, or to have them separate in the output.

- The **maximum number of articles** can be limited to consume less tokens and to restrict the search.

- **Source location** can be specified to find articles that were written by news sources located in the given geographic location. Location URI can either be a city or a country.

- **Event location** can be specified to select articles that took place in a specific geographic location (as indicated in the Dateline). Location URI can either be a city or a country.

- By setting the **percentile of top sources** to a value lower than 100, sources will be selected according to the <a href="https://www.alexa.com/siteinfo" target="_blank">**global Alexa ranking**</a>. For example, by setting the value to 20, research will be limited to top ranking news sources so that the resulting number of articles will be approximately 20% of all content that would be received without the filter.

- The last field in the form can be used to define **Complex Queries**. If used, it will overwrite the other query parameters (please fill in the mandatory form fields in any case, even if they will be ignored). More information about how to define complex queries is provided [here](https://github.com/EventRegistry/event-registry-python/). An example follows:

  ```python
  {
  "$query": {
      "$and": [
          {
              "keyword": {
                  "$or": ["home", "house"]
              }
          },
          {
              "keyword": {
                  "$or": ["energy", "heathing"]
              }
          },
          {
              "lang": "eng",
              "dateStart": "2021-01-20",
              "dateEnd": "2021-02-08",
              "sourceUri": {
                  "$or": [ "ft.com", "nytimes.com" ]
              },
              "sourceLocationUri": {
                  "$or": [ 'http://en.wikipedia.org/wiki/United_States' ]
              },
              "locationUri": {
                  "$or": [ 'http://en.wikipedia.org/wiki/United_States' ]
              }
          }
      ],
      "$not": {
          "keyword": {
              "$or": ["covid"]
          }
      }
      },
      "$filter": {
          "isDuplicate": "skipDuplicates",
          "startSourceRankPercentile": 0,
          "endSourceRankPercentile": 100,
          "dataType": ["news", "pr", "blog"]
      }
  }
  ```

> #### Run
> Starts the fetcher and collects the articles that match the search query. Articles can be downloaded and subsequently uploaded in the app for the analysis. In case of errors, the fetcher can also be **stopped**.
>
> #### Output
>
> A CSV file where the char "|" is used as separator.