# RSS-GPT

[![](https://img.shields.io/github/last-commit/yinan-c/RSS-GPT/dev?label=updated)](https://github.com/yinan-c/RSS-GPT/tree/dev)
[![](https://img.shields.io/github/last-commit/yinan-c/RSS-GPT/main?label=feeds%20refreshed)](https://yinan-c.github.io/RSS-GPT/)
[![](https://img.shields.io/github/license/yinan-c/RSS-GPT)](https://github.com/yinan-c/RSS-GPT/blob/master/LICENSE)


## What is this?

[Configuration Guide](https://yinan-c.github.io/rss-gpt-manual-en.html) | [中文简介](README-zh.md) | [中文教程](https://yinan-c.github.io/rss-gpt-manual-zh.html)

Using GitHub Actions to run a simple Python script repeatedly: Calling OpenAI API to generate summaries for RSS feeds, and push the generated feeds to GitHub Pages. Easy to configure, no server needed.

### Features

- Use ChatGPT to summarize RSS feeds, and attach summaries to the original articles, support custom summary length and target language.
- Aggregate multiple RSS feeds into one, remove duplicate articles, subscribe with a single address.
- Add filters to your own personalized RSS feeds.
- Host your own RSS feeds on GitHub repo and GitHub Pages.

![](https://i.imgur.com/7darABv.jpg)

## Quick configuration guide

- Fork this repo
- Add Repository Secrets
    - U_NAME: your GitHub username
    - U_EMAIL: your GitHub email
    - WORK_TOKEN: your GitHub personal accesstoken with `repo` and `workflow` scope, get it from [GitHub settings](https://github.com/settings/tokens/new)
    - OPENAI_API_KEY(OPTIONAL, only needed when using AI summarization feature): Get it from [OpenAI website](https://platform.openai.com/account/api-keys)
- Enable GitHub Pages in repo settings, choose deploy from branch, and set the directory to `/docs`.
- Configure your RSS feeds in config.ini

You can check out [here](https://yinan-c.github.io/rss-gpt-manual-en.html) for a more detailed configuration guide.

## ChangeLog and updates

- There is a [`dev` branch](https://github.com/yinan-c/RSS-GPT/tree/dev) for manual updates on the script, auto commits will no longer be pushed to this `dev` branch. The purpose of doing this is to separate the manual updates and auto commits, so that it is easier to check the updates and pull to your repo.
- As OpenAI released a new version of `openai` package on Nov 06, 2023.  [More powerful models are coming](https://openai.com/blog/new-models-and-developer-products-announced-at-devday), the way to call API also changed. As a result, the old script will no longer work with the latest version installed, and needs to be updated. Otherwise, you will have to set `openai==0.27.8` in `requirements.txt` to use the old version.
-  In the latest updates, **contexts longer than 16k tokens are no longer truncated, instead, will use the `gpt-4-1106-preview` model.** If you don't like this, let me know and I'll think about adding customizability to choose whether truncate or use `gpt-4-1106-preview` model.
- Check out the [CHANGELOG.md](CHANGELOG.md).

### Contributions are welcome!

- Feel free to submit issues and pull requests. Please submit pull requests to the `dev` branch.

## Example feeds being processed

These feeds on hosted in the [`docs/` subdirectory](https://github.com/yinan-c/RSS-GPT/tree/main/docs) in this repo as well as on my [GitHub Pages](https://yinan-c.github.io/RSS-GPT/). Feel free to subscribe in your favorite RSS reader.

I will consider hosting more feeds in the future. Email me or submit an issue if there is any question using the script or any suggestions.

- http://rss.packetstormsecurity.com/ -> https://DCKento.github.io/RSS-GPT/Packet_Storm.xml
- https://www.proofpoint.com/us/threat-insight-blog.xml -> https://DCKento.github.io/RSS-GPT/Proofpoint_Threat_Insight.xml
- http://feeds.arstechnica.com/arstechnica/index/ -> https://DCKento.github.io/RSS-GPT/Ars_Technica.xml
- http://www.us-cert.gov/channels/alerts.rdf -> https://DCKento.github.io/RSS-GPT/US_CERT_Cyber_Security_Alerts.xml
- http://feeds.feedburner.com/tripwire-state-of-security -> https://DCKento.github.io/RSS-GPT/The_State_of_Security.xml
- https://malware.news/c/news/8.rss -> https://DCKento.github.io/RSS-GPT/Malware_News.xml
- http://thehackernews.com/feeds/posts/default -> https://DCKento.github.io/RSS-GPT/The_Hacker_News.xml
- https://www.ncsc.gov.uk/blogs-feed.xml -> https://DCKento.github.io/RSS-GPT/NCSC_Blog_Feed.xml
- http://securelist.com/feed/ -> https://DCKento.github.io/RSS-GPT/Securelist.xml
- http://googleonlinesecurity.blogspot.com/feeds/posts/default?alt=rss -> https://DCKento.github.io/RSS-GPT/Google_Online_Security_Blog.xml
- https://www.cisecurity.org/feed/alert -> https://DCKento.github.io/RSS-GPT/Cyber_Threat_Alert.xml
- http://www.microsoft.com/technet/security/bulletin/secrss.aspx -> https://DCKento.github.io/RSS-GPT/Microsoft_Security_Bulletins.xml
- http://www.reddit.com/r/netsec/.rss -> https://DCKento.github.io/RSS-GPT/Technical_Info_Security_Content_Discussion.xml
- http://isc.sans.org/rssfeed.xml -> https://DCKento.github.io/RSS-GPT/SANS_Internet_Storm_Center.xml
- http://blog.portswigger.net/feeds/posts/default -> https://DCKento.github.io/RSS-GPT/PortSwigger_Web_Security_Blog.xml
