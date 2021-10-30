# deploy

## After cloning this repository:

1. Create .env file and fill it in like in the example default.env

2. Type these commands in the command line (be sure that you are in the deploy package):

    ```- docker-compose up -d```

    ```- docker-compose exec backend python -m service.database.models```

3. You need to add some walls from VK to the DB first, which from you will get new posts and emotion color for them after. You may do it one of these ways:

    - From the TG BOT, type the command in this format - ```/setwall wall_link``` (example of wall_link is https://vk.com/wall-[wall])

    - From the Insomnia client, you can make the POST query to this route http://localhost:5000/api/v1/walls with this json body:  { "wall": "-30666517", "link": "https://vk.com/wall-[wall]", "uid": "-1"} 
    uid - is last_post_id for this wall, settind it as "-1" is made for being sure that any post will be new and saved to the DB.

4. Using the TG BOT,

    - You can get the emotion color for your text directly from the emotion recogniser service, typing this command - ```/predict text``` (any text you like)

    - You can get posts from the current wall with emotion color you are setting, typing this command - ```posts/ wall_id emotion``` (as an example, wall_id:-30666517, emotion:positive, 
    ```/posts -30666517 positive```). There are 5 type of emotions you can chose and get (*positive, negative, neutral, skip or speech*)

*Much thanks to **theese guys**, we are currently using the model which was trained on their dataset!*

```
@inproceedings{rogers-etal-2018-rusentiment,
    title = "{R}u{S}entiment: An Enriched Sentiment Analysis Dataset for Social Media in {R}ussian",
    author = "Rogers, Anna  and
      Romanov, Alexey  and
      Rumshisky, Anna  and
      Volkova, Svitlana  and
      Gronas, Mikhail  and
      Gribov, Alex",
    booktitle = "Proceedings of the 27th International Conference on Computational Linguistics",
    month = aug,
    year = "2018",
    address = "Santa Fe, New Mexico, USA",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/C18-1064",
    pages = "755--763",
}```
