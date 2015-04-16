# News Snapshot  Gold Standard

The gold standard is composed by a set of 5 short videos from the [BBC One Minute World News Website ](http://www.bbc.com/news/video_and_audio/) which have been annotated with a list of Named Entities that illustrate the different facts depicted in them. Each named entity has an associated score normalized from _-1_ to _1_ in order to indicate its importance of that entity inside the whole context of the video.

+ Entities and scores per video are available in folder [data](https://github.com/jluisred/NewsEntities/tree/master/data)
+ Metodology is explained in Section [Metodology](https://github.com/jluisred/NewsEntities#methodology-for-groundtruth-generation) below
+ [Videos](https://github.com/jluisred/NewsEntities/tree/master/videos) and [transcripts](https://github.com/jluisred/NewsEntities/tree/master/transcripts) are included in corresponding folders.
+ You can read our [paper](https://github.com/jluisred/NewsEntities/tree/master/papers/icwe2015) in how to automatically recreate those entities by relying on a Web document expansion approach.
+ Gold Standard data is also shown [below](https://github.com/jluisred/NewsEntities#gold-standard-data).

# Methodology for GroundTruth Generation

We selected 5 short videos from the [BBC One Minute World News Website ](http://www.bbc.com/news/video_and_audio/). Each video lasted from 1 to 3 minutes. The selection covered a wide range of subjects specifically: politics, armed conflicts, environmental events, legal disputes, and social news. The intention behind this topic choice was to fit international audiences, since we planned to perform a user study with international participants. 
Subtitles of the videos were not available; therefore, a member of the team manually transcribed the speech in the videos.  After obtaining the transcriptions, the following steps were performed in order to obtain a set of unbiased candidate entities. We chose to focus only on entities of the types person, organisation and location because they can directly translate or answer three questions: Who is involved? What happened? Where did it take place? These questions are a subset taken from a well known concept in journalism known as the 5Ws (_who_, _what_, _when_, _where_ and _why_), which emphasizes the fundamental dimensions that an informative journalistic text should report on. Regarding the questions _when_ and _why_, there where discarded because in order to acquire meaningfulness they need to be modeled not only by single entities but also by more complex relations between them that are out of the scope of the current paper.


## Subtitles
All entities of the type person, organisation and location were manually extracted from each one of the video subtitles and added to the unfiltered list of entities (candidate set). 

## Image in the video
The video image was visually analysed by a researcher and every time a recognisable person, organisation or location was portrayed this was also added as an entity to the candidate set. 

## Text in the video image
The video was analysed for text appearing in the image. Whenever text appeared in the video image, for example in the form of nametag overlays, the named entities appearing in such tags were added to the candidate set. 

## Related entities
In order to complement the candidate set with entities that might be interesting for the user, but are not necessarily found in the videos, we used the following two strategies:

## Suggestions of an expert
We collaborated with a journalist with more than 6 years of experience as a writer/editor for important American newspapers and websites.  We configured an online survey to retrieve the expert’s feedback. In the survey we explained what named entities are and which types of named entities we needed. After this introduction we presented the videos to the expert. Following each one we asked him to list the named entities that, according to his criteria, would better serve the objective of showing interesting additional information to the users. The expert didn’t have access to the candidate set, and was completely free to suggest any named entity he wanted. 

## Related articles
We used Google custom search to look for articles related to the video in three news sources: The Guardian, New York Times, and Al Jazeera online (English). We performed this search using the main terms in the videos’ title, for example, for _Fugitive Edward Snowden applies for asylum in Russia_ we searched for  _Edward_ + _Snowden_ + _asylum_ + _Russia_. We limited the results to + - 3 days from the day when the video was published. We chose one document from each source, the one closest in topic and time to the video. We then extracted all named entities of the types person, organisation and location from the resulting documents. In order to keep the entities within a reasonable number for inclusion in a survey, we kept only the named entities that appeared in at least 2 related articles and dropped all the ones that only appeared in one.  The selected entities were added to the candidate set. 

## Refining the candidate set
We refined the candidate set  comprised of all found entities by eliminating all duplicated named entities and standardising names. For example, when we had ``Barack Obama'' as an entity and ``Obama'' as another entity we eliminated the shorter one and left the complete name. 

A total of 99 entities were obtained from all videos. For a distribution of entities among types and videos please see next Table :


Newscast Title  | Date  | Person  | Organization  | Location  | Total
------------- | ------------- | ------------- | ------------- | ------------- | -------------
Fugitive Edward Snowden applies for asylum in Russia  | 2013-07-03  | 11  | 7  | 10  | 28
Egypt’s Morsi Vows to Stay in Power | 2013-07-23  | 4  | 5  | 4  | 17
Fukushima leak causes Japan concern | 2013-07-24  | 7  | 5  | 5  | 13
Rallies in US after Zimmerman Verdict | 2013-07-17  | 9  | 2  | 8  | 19
Royal Baby Prince Named George  | 2013-07-15  | 15  | 2  | 6  | 22
Total  |    | 46  | 20  | 33  | 99



## Online Survey
We created an online survey with the aim of gathering information about the degree of interestingness of the entities in the candidate set. Based in \cite{vonBrzeski:2007:LCU:1321440.1321537} we define interestingness as to whether an entity is interesting, useful or compelling enough to tear the user away from the main thread of the document. 

Fifty international subjects participated in this online study. They responded an online call distributed via email and social networks. Their age range was between 25 and 54 years with an average age of 30.3 (standard deviation 7.3 years). 18 participants were female and 32 were male. Most of the participants were highly educated and 48 of them had either a university bachelor degree or a postgraduate degree. The main requisite for participation was that they were interested in the news and followed the news regularly, preferably through means that include newscasts.
During the interview participants were asked to choose at least 3 out of 5 videos according to their preferences. Then they were shown each one of the videos. After each video, they were asked to rate whether they would be interested in receiving more information about the named entities in the context of the news video and on a second screen or similar application. All the named entities from the candidate set related to the last seen video were shown in a list with ratio buttons arranged in a similar way to a three-point Likert-scale. The possible answers were _Yes_ _Maybe_ and _No_. 

## Further details on the online survey

The number of respondents per video were: _Snowden_ 49, _Morsi_ 34, _Fukushima_ 42, _Zimmerman_ 27, and _Royal baby_ 15.

In order to calculate the interestingness scores from the users’ responses, we gave every answer a numerical value: _Yes_ = 1, _Maybe_ = 0 and _No_ = -1.  We then obtained an average score for each entity using the number of participants that rated an entity and the score that each participant gave to that particular entity.  This average was used to obtain a ranking of all the entities in the candidate set according to user preferences. 

With the objective of finding out users preferences regarding the three analysed entity types: _person_, _organization_ and _location_, we calculated an average rating for each one of the entity types. The results in descending order were: organisation = -0,05, person = -0,24  and location = -0,52. These results clearly show a preference from users for the entities of the type organisation and person over those of the type location.
\end{document}

# Gold Standard Data

Here the different entities that compose the 

## Video 1: Fugitive Edward Snowden applies for asylum in Russia 
Entity Label  | Score  
------------- | ------------- 
Edward Snowden | 0.5555556
National Security Agency | 0.3777778
Central Intelligence Agency | 0.0666667
Glenn Greenwald | 0.0666667
Foreign Intelligence Surveillance Court | 0
Booz Allen Hamilton | -0.1333333
Laura Poitras | -0.2666667
Barton Gellman | -0.3111111
Verizon Wireless | -0.3333333
Angela Merkel | -0.3777778
Anatoly Kucherena | -0.4
Federal Migration Service | -0.4444444
US State Department | -0.4444444
Vladimir Putin | -0.4666667
Sheremetyevo International Airport | -0.4666667
Nicaragua | -0.4888889
Evo Morales | -0.4888889
Patrick Ventrell | -0.5111111
Moscow | -0.5555556
Bolivia | -0.5777778
Kremlin | -0.6
Russia | -0.6222222
Venezuela | -0.6222222
United States of America | -0.6666667
Latin America | -0.7333333
Barack Obama | -0.7555556
Jay Carney | -0.7555556
South America | -0.8


## Video 2: Egypt’s Morsi Vows to Stay in Power.
URL: http://www.bbc.com/news/world-middle-east-23156103

Entity Label  | Score  
------------- | ------------- 
Muslim Brotherhood | 0.441176471
Mohamed Morsi | 0.352941176
Islamist Nour Party | 0.323529412
Arab Spring | 0.264705882
Egypt opposition alliance | 0.235294118
Abdul Fattah Sisi | 0.088235294
Hosni Mubarak | -0.029411765
Adly Mansour | -0.176470588
Tahrir Square | -0.235294118
Mohamed ElBaradei | -0.235294118
Supreme Constitutional Court | -0.294117647
Egypt | -0.352941176
Cairo | -0.470588235
Cairo University | -0.470588235
Nasr | -0.529411765
Jeremy Bowen | -0.705882353
Nisha Pilla | -0.882352941

## Video 3: Fukushima leak causes Japan concern 
URL: http://www.bbc.com/news/world-asia-pacific-23425570

Entity Label  | Score  
------------- | ------------- 
Fukushima Daiichi | 0.5
Tokyo Electric Power Company | 0.476190476
Reactor building no 3 | 0.404761905
Nuclear Regulation Authority | 0.142857143
Pacific Ocean | -0.357142857
Nuclear Regulatory Commission | -0.357142857
Japan | -0.380952381
Naomi Hirose | -0.476190476
Tokyo | -0.5
Shunichi Tanaka | -0.523809524
Shinzo Abe | -0.547619048
Rupert Wingfield Hayes | -0.785714286
TV Tokyo | -0.880952381

## Video 4: Rallies in US after Zimmerman Verdict
URL: http://www.bbc.com/news/world-us-canada-23312559

Entity Label  | Score  
------------- | ------------- 
George Zimmerman | 0.444444444
Trayvon Martin | 0.407407407
National Association for the Advancement of Colored People (NAACP) | -0.037037037
Rachel Jeantel | -0.185185185
General Eric Holder | -0.222222222
Rev. Lowman Oliver | -0.259259259
Mark OMara | -0.259259259
Sanford | -0.333333333
Angela Corey | -0.37037037
United States Department of Justice | -0.407407407
Matt Gutman | -0.555555556
Barack Obama | -0.592592593
New York | -0.666666667
Florida | -0.666666667
Los Angeles | -0.703703704
San Francisco | -0.740740741
Times Square | -0.740740741
Washington DC. | -0.814814815
United States of America | -0.851851852

## Video 5: Royal Baby Prince Named George 
URL: http://www.bbc.com/news/uk-23429644

Entity Label  | Score  
------------- | ------------- 
Kate Middleton Duchess of Cambridge | 0.357142857
King George the VI Bertie | 0.357142857
Prince George of Cambridge George Alexander Louis | 0.285714286
Prince William Duke of Cambridge | 0.285714286
King George V | 0.142857143
Queen Elizabeth | 0.071428571
Earl Louis Mountbatten | -0.142857143
Prince Harry of Wales | -0.214285714
Charles Prince of Wales | -0.285714286
Queen Victoria | -0.285714286
Balmoral Castle | -0.285714286
Princess Margaret | -0.357142857
Cambridge | -0.357142857
Queen Mary of Teck | -0.357142857
Kensington Palace | -0.428571429
The Queen Mother Elizabeth Angela Marguerite Bowes-Lyon | -0.428571429
Irish Republican Army | -0.428571429
St Mary's Hospital | -0.5
England Country | -0.5
Great Britain | -0.5
Suzannah Lipscomb | -0.571428571
