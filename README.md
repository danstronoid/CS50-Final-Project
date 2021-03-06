# TWITTER CHIMES 
*CS50x Final Project*
by Daniel Schwartz

Twitter chimes takes an incoming Twitter stream and uses the data from the stream to create sound in a musical context, much like a traditional set of windchimes.  The idea is to create an audible and pleasant representation of the stream data.  In this case I'm using Twitter as the source of the stream, but any real-time stream data could be used.

The stream is created using Twitter's standard streaming API and the 'twitter-lite' package.  The keyword "wind" is used to filter the stream and track any mentions of the word.  Using 'socket.io' (which uses a combination of long polling and web socketing), the stream is then distributed to the client.  A server application, implemented using express and node.js, handles creating the stream, initializing the socket, and rendering templates.

On the client side, a frequency-modulated synthesizer is created using the Web Audio API.  Upon receiving a stream event, the playback function is called utilizing some of the data from the tweet to control parameters of the synthesizer.  Some of the parameters are randomized to create a more interesting and musical playback.  It is worth noting that the playback function creates a new oscillator every time it is called, which avoids running into a limit on the number of simultaneous voices.  The user is provided with several controls to alter the sound of the synth, including volume, reverb amount, modulation depth, oscillator wave-type, and musical tonality.  

The user is also able to view the incoming tweets using Twitter's embedded widget.  The number of tweets shown at a given time is limited.  This could alternatively be implemented using an embedded timeline which would have to be curated by an account.

Check it out: https://twind-chimes.herokuapp.com/