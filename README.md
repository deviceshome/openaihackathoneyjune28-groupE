# openaihackathoneyjune28-groupE

**Problem Statement**
Title: Enhancing User Experience with Netflix Movie Titles and Reviews through Chatbot Interaction

Background:
Netflix offers a vast library of movies, which can be overwhelming for users to navigate. Users often spend a significant amount of time browsing through titles, seeking information about the movies, and looking for reviews to make informed decisions about what to watch. The current process can be time-consuming and may not always lead to satisfactory viewing choices.

Problem:
Users need a more streamlined and interactive way to access information about Netflix movie titles and reviews without having to manually search through the platform or external review sites. The lack of immediate assistance and personalized recommendations can lead to user frustration and a suboptimal viewing experience.

Solution:
Implement a chatbot that integrates with Netflix's database to provide users with instant access to movie titles, descriptions, and aggregated reviews. The chatbot will use natural language processing to understand user queries and respond with relevant information. It will also offer a feature to rate movies and provide feedback, enhancing the recommendation system for future interactions.

**Collecting Data:**

We collected open data from <https://www.kaggle.com/datasets/shivamb/netflix-shows?select=netflix_titles.csv> which has netflix movies titles and content. we transformed the data into combined objects of reviews 

```json
 {
      "@search.score": 3.733027,
      "@search.rerankerScore": 2.088019847869873,
      "@search.captions": [
        {
          "text": "Netflix Afterparty: The Best Shows of The Worst Year  David Spade, London Hughes, Fortune Feimster United States December 13, 2020 2020 TV-MA 59 min Comedies David Spade, Fortune Feimster and London Hughes welcome guests from \"Tiger King,\" \"Emily in Paris,\" \"The Queen's Gambit\" and more Plus: Kevin Hart.  s1555 TV Show Children of Adam  Maguy Bou G...",
          "highlights": "Netflix Afterparty: The Best Shows of The Worst Year<em>  David Spade, London Hughes, Fortune Feimster</em> United States December 13, 2020 2020 TV-MA 59 min Comedies<em> David Spade, Fortune Feimster</em> and London Hughes welcome guests from \"Tiger King,\" \"Emily in Paris,\" \"The Queen's Gambit\" and more Plus: Kevin Hart.  s1555 TV Show Children of Adam  Maguy Bou G..."
        }
      ],
      "content": "s1550\tMovie\tThe Professor and the Madman\tFarhad Safinia\tMel Gibson, Sean Penn, Natalie Dormer, Eddie Marsan, Steve Coogan, Stephen Dillane, Ioan Gruffudd, Jennifer Ehle, Jeremy Irvine, David O'Hara, Anthony Andrews\tIreland, France, Iceland, United States, Mexico, Belgium, United Kingdom, Hong Kong\tDecember 15, 2020\t2019\tTV-14\t125 min\tDramas, Independent Movies\tWhile working on the first Oxford English Dictionary, a scholar receives thousands of entries from a doctor with a lengthy vocabulary and dark secrets.\n\ts1551\tMovie\tA California Christmas\tShaun Paul Piccinino\tLauren Swickard, Josh Swickard, Ali Afshar, David Del Rio, Natalia Mann, Katelyn Epperly, Gunnar Anderson, Julie Lancaster, Amanda Detmer\tUnited States\tDecember 14, 2020\t2020\tPG-13\t107 min\tComedies, Romantic Movies\tWith his carefree lifestyle on the line, a wealthy charmer poses as a ranch hand to get a hardworking farmer to sell her family’s land before Christmas.\n\ts1552\tTV Show\tHilda\t\tBella Ramsey, Ameerah Falzon-Ojo, Oliver Nelson, Daisy Haggard, Rasmus Hardiker\tUnited Kingdom, Canada, United States\tDecember 14, 2020\t2021\tTV-Y7\t2 Seasons\tKids' TV\tFearless, free-spirited Hilda finds new friends, adventure and magical creatures when she leaves her enchanted forest home and journeys to the city.\n\ts1553\tTV Show\tTiny Pretty Things\t\tLauren Holly, Kylie Jefferson, Casimere Jollette, Brennan Clost, Barton Cowperthwaite, Bayardo De Murguia, Damon J. Gillespie, Anna Maiche, Daniela Norman, Michael Hsu Rosen, Tory Trowbridge\tUnited States\tDecember 14, 2020\t2020\tTV-MA\t1 Season\tTV Dramas, TV Mysteries, TV Thrillers\tWhen an attack brings down the star student at an elite ballet school, her replacement enters a world of lies, betrayal — and cutthroat competition.\n\ts1554\tMovie\tThe Netflix Afterparty: The Best Shows of The Worst Year\t\tDavid Spade, London Hughes, Fortune Feimster\tUnited States\tDecember 13, 2020\t2020\tTV-MA\t59 min\tComedies\tDavid Spade, Fortune Feimster and London Hughes welcome guests from \"Tiger King,\" \"Emily in Paris,\" \"The Queen's Gambit\" and more. Plus: Kevin Hart.\n\ts1555\tTV Show\tChildren of Adam\t\tMaguy Bou Ghosn, Daniella Rahme, Maxim Khalil, Qays Sheikh Najib, Mohamed Yaghy, Rodney Haddad, Nada Abou Farhat\tLebanon\tDecember 12, 2020\t2020\tTV-14\t1 Season\tInternational TV Shows, TV Dramas, TV Thrillers\tAmid crime and corruption, the lives of two couples intertwine as unexpected events soon reveal their dark secrets and tainted pasts.\n\ts1556\tTV Show\tGrizzy et les Lemmings\t\tPierre-Alain de Garrigues, Josselin Charier\tFrance\tDecember 12, 2020\t2018\tTV-Y\t2 Seasons\tKids' TV, TV Comedies\tStrong, whip-smart Grizzy rules a Canadian forest, where he has his paws full with a family of frolicsome lemmings.\n\ts1557\tMovie\tA Trash Truck Christmas\tEddie Rosas\tHenry Keane, Glen Keane, Lucas Neff, Brian Baumgartner, Jackie Loeb, John DiMaggio\t\tDecember 11, 2020\t2020\tTV-Y\t28 min\tChildren & Family Movies\tWhen Santa crash-lands in the junkyard on Christmas Eve, Hank, Trash Truck and their animal friends all have a hand in rescuing the holiday for everyone.\n\ts1558\tMovie\tCanvas\tFrank E. Abney III\t\tUnited States\tDecember 11, 2020\t2020\tG\t9 min\tChildren & Family Movies, Dramas\tAfter a heartbreaking loss, a grandfather struggling to reclaim his passion for painting finds the inspiration to create again.\n\ts1559\tMovie\tGiving Voice\tJames D",
      "filepath": "netflix_titles.txt",
      "title": "show_id\ttype\ttitle\tdirector\tcast\tcountry\tdate_added\trelease_year\trating\tduration\tlisted_in\tdescription",
      "url": "https://eyuser28.blob.core.windows.net/fileupload-netflix/netflix_titles.txt",
      "id": "aHR0cHM6Ly9leXVzZXIyOC5ibG9iLmNvcmUud2luZG93cy5uZXQvbmV0ZmxpeC1jaHVua3MvYUhSMGNITTZMeTlsZVhWelpYSXlPQzVpYkc5aUxtTnZjbVV1ZDJsdVpHOTNjeTV1WlhRdlptbHNaWFZ3Ykc5aFpDMXVaWFJtYkdsNEwyNWxkR1pzYVhoZmRHbDBiR1Z6TG5SNGRBMi9jb250ZW50X2NodW5rc18xODMuanNvbg2",
      "chunk_id": "183",
      "last_updated": "20240628071431"
    }
```

We have converted data into chunks.

**Building RAG with your own Data**

We have used azure open ai playground to deploy gpt 3.5 turbo model and datasource with upload options into the storage account. We have give the system a message of "You are an AI assistant to provide moview review"

<img width="1783" alt="image" src=".\netflix\hack4.PNG">


**Deploying the Model and Consuming in client application**

We used webapp deploy option available in playground with F1 tier, which was then deployed to <https://adiaiwebapp.azurewebsites.net>

**Examples:**

We have tried following examples and system started responding with right results with citation.

1.How many movie titles in database?
2.How many PG-13 movies with you?
3. Which mvie is based on blackhole of universe?
<img width="1792" alt="image" src=".\netflix\hack1.PNG">
<img width="1792" alt="image" src=".\netflix\hack3.PNG">
<img width="1792" alt="image" src=".\netflix\hack5.PNG">








