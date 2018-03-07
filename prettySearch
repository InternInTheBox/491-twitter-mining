import twitter
from vaderSentiment.vaderSentiment import sentiment as vaderSentiment
from prettytable import PrettyTable

def removeUnicode(text):
        asciiText = ""
        for char in text:
            if (ord(char) < 128):
                asciiText = asciiText + char

        return asciiText

#Variables that contains the user credentials to access Twitter API 
consumer_key = 'LcyEklw3dF26p3kjm3ZTUrIy1'
consumer_secret = 'PPEVKrbxfCNhOs6S17lsMI3DIO5wsvs2hNY7CXU7i44RT7QndO'
oauth_token = '963907468005986310-8GcOdsEP4bYr4hBYWaSyURd2KoC9L9Z'
oauth_token_secret = '4UOJ5dcZIy77Nf4pLzkUICCMtUPIJjqZOEpMWgUNdPHZp'


auth = twitter.oauth.OAuth(oauth_token, oauth_token_secret, consumer_key, consumer_secret)

tw = twitter.Twitter(auth=auth)

# Search

q = ['Pepsi', 'CocaCola']
tables = []
count=25
tweets = tw.search.tweets(q=q, count=count, lang='en')
texts=[]
sentim = []

for x in range(0, len(q)):
	tables.append(PrettyTable())
	tables[x].field_names = [q[x] + " Tweets", "Sentiment Analysis", "Lexical Analysis"]

	for status in tweets['statuses']:
	    texts.append(status["text"])
	    vs = vaderSentiment(status["text"].encode('utf-8'))
	    sentim.append(str(vs['compound']))

	num = 0
	for text in texts:
	    words = []
	    string = ""
	    for w in text.split():
	        words.append(w)
	    	string += w + " "
	    tables[x].add_row([string, sentim[num], 1.0*len(set(words))/len(words)])
	    num = num + 1

	print(tables[x])
