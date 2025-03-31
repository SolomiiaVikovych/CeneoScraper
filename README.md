# CeneoScraper

## Algorithm for extratimg opinions about single product from Ceneo.pl
1. send  the request for accesing first webpage with opinions about product
2. if resposnse is OK, parse HTML page content into DOM structure
3. Extract opinions and their components  from DOM structure
4. Assign opinions with their components to complex data structure
5. if there're more pages with opinions, repeat steps 1-5 
6. Save data structures with opinions ito database

## Structure of single opinion in Ceneo.pl
|Component|Variable|Selector|
|---------|--------|--------|
|opinion|opinion|div.js_product-review:not(.user-post--highlight)|
|opinion ID|opinion_id|["data-entry-id"]|
|opinion’s author|author|spam.user-post__autjor-name|
|author’s recommendation|recommend|spam.user-post__autjor-recomendation>em|
|score expressed in number of stars|stars|span.user-post__score-count|
|opinion’s content|content|.class="user-post__text"|
|list of product advantages|pros|div.review-feature__item--positive|
|list of product disadvantages|cons|iv.review-feature__item--negative|
|how many users think that opinion was helpful|up_votes|button.vote-yes["data-total-vote"]|
|how many users think that opinion was unhelpful|down_votes|button.vote-no["data-total-vote"]|
|publishing date|published|span.user-post__published > time:nth-child(1)["datetime"]|
|purchase date|purchased|span.user-post__published > time:nth-child(2)["datetime"]|