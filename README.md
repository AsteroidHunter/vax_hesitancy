# Avax tweets dataset
The repository contains two data sets associated with vaccine hesitancy on Twitter. The "streaming" data set contains tweets collected by leveraging Twitter streaming API to listen to the set of anti-vaccine keywords. You can see the full list of these keywords in keywords.txt. The "user-oriented" data set contains historical tweets of users who are susceptible to anti-vaccine narratives. To comply with [Twitter's Term of Service](https://twitter.com/en/tos), only tweet IDs are released. The data is for non-commercial research purposes only. It is our hope that it will help those who are studying and tracking anti-vaccine misinformation on social media and enable the understanding of public vaccine hesitancy more.

The associated paper to this repository can be found here: (link to the paper).

## Data Organization
The "streaming-tweetids" folder corresponds to the streaming data set whereas the "user-oriented-tweetids" folder corresponds to the user-oriented data set. All the files are named by numbers starting from 0 and are in the .txt form.

## Notes about the data
1. Only English tweets are considered.
2. The overview of two data sets are summarized in below:
   1. Streaming data set
        | Attribute      | Value |
        | ----------- | ----------- |
        | Number of tweets      | 716,672 |
        | Number of users   | 268,582 |
        | Verified accounts      | 3,104 |
        | Average tweet per user   | 2.7 |
        | User with location      | 1,311 |
        | Oldest tweet   | 2010-10-19 |
        | Most recent tweet   | 2021-02-03 |
    2. User-oriented data set
        | Attribute      | Value |
        | ----------- | ----------- |
        | Number of tweets      | 120,058,028 |
        | Number of users   | 78,958 |
        | Verified accounts      | 298 |
        | Average tweet per user   | 1520.5 |
        | User with location      | 373 |
        | Oldest tweet   | 2007-03-06 |
        | Most recent tweet   | 2021-02-03 |
3. You may consider using tools such as the Hydrator and Twarc to rehydrate the Tweet IDs. For detailed instructions please see the next section.

## How to Hydrate
### Hydrating using Hydrator (GUI)
Navigate to the Hydrator github repository and follow the instructions for installation in their README. As there are a lot of separate Tweet ID files in this repository, it might be advisable to first merge files from timeframes of interest into a larger file before hydrating the Tweets through the GUI.

### Hydrating using Twarc (CLI)
Many thanks to Ed Summers (edsu) for writing this script that uses Twarc to hydrate all Tweet-IDs stored in their corresponding folders.

First install Twarc and tqdm
```
pip3 install twarc
pip3 install tqdm
```

Configure Twarc with your Twitter API tokens (note you must apply for a Twitter developer account first in order to obtain the needed tokens). You can also configure the API tokens in the script, if unable to configure through CLI.
```
twarc configure
```
Run the script. The hydrated Tweets will be stored in the same folder as the Tweet-ID file, and is saved as a compressed jsonl file
```
python3 hydrate.py
```