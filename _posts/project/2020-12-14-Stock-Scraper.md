---
layout: post
title: Stock Scraper
date: 2020-12-14
category: project
---

최근 주식에 관심을 가지게 되어 python을 이용해 주식 정보를 가져오는 프로그램을 만들었다.

**<https://github.com/iamhabi/Stock-Scraper>**

exchange_rate.py는 환율 정보를 가져온다.  
gold.py는 금값의 시세를 가져온다.  
main_news.py는 네이버에서 주식 주요 뉴스를 가져온다.  
stock_market.py는 KOSPI와 NASDAQ 등 주가지수의 최근 10일간의 정보를 가져온다.  
sise_day.py는 해당 주식의 최근 10일간의 정보를 가져온다.  
news.py는 해당 주식의 최근 10개의 뉴스를 가져온다.

가져온 정보들은 모두 json형식으로 stock.json에 저장된다.