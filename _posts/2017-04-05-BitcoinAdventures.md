---
layout: post
title:  "Bitcoin Adventures"
image: ''
date:   2017-04-05 00:00:01
tags:
- project
description: 'My forays into Bitcoin'
categories:
- Projects
---

I remember the first time I had heard of bitcoin. It was 6:30 in the morning, and I was sitting in a student lounge in high school. Surfing my usual tech blogs, I uncovered an article about creating money on your computer by "mining". At the time, I passed it off as a ludicrous idea - and moved on to the next article...

Fast forward 5 years. Now at MIT, the topic of cyptocurrencies was a hot topic again! I made my first purchase of bitcoin with my good friend Will one summer afternoon. I was a proud owner of BTC! The burgeoning trader in me justified that supply and demand dictated the price of bitcoin had to go up - afterall less supply => greater demand => higher price. We bought a couple more. As any good trade pans out - it is always a regret of not buying enough. During BTC's rise in early 2013, we had netted a small profit, enough to go for a nice dinner, but nothing to write home about - we sold, had said nice dinner, and called it a fun adventure.

Fast forward another year - now in my tenure at Morgan Stanley, Bitcoin once again took headlines - rocketing to over $1000. I was again intrigued, but this time from a statistical arbitrage perspecive. At the time, there were only a few exchanges that allowed for trading of Bitcoin, and they were always out of sync, sometimes by a few percentage points. I spent a weekend hacking away at an arbitrage script to automate trading of BTC on two different exchanges (amazingly they both had APIs). 

Here was the main (extremely simple) arbitrage function. We could set a threshold (taking into account trading fees, etc.) The two exchanges were Cryptsy and Bter. I would leave this running overnight, and the next morning, I could see a visual log of all of the trades done.

{% highlight python %}

def arb_trade(pair, thresh, arb_amount):
    cname = currency_dict[pair]
    curr = pair[:3]
    cbuy = ctopbuy(cname)
    csell = ctopsell(cname)
    bbuy = btopbuy(pair)
    bsell = btopsell(pair)
    print "starting analysis"
    if csell[1]*(1+thresh)<bbuy[1]:  #Buy on Cryptsy, sell on Bter
        max_sell = bter_balance(curr)
        if max_sell>arb_amount and min(bbuy[0],csell[0])>arb_amount*1.5:
            bter_exchange.placeOrder(pair, 'sell', bbuy[1], arb_amount)
            exchange.buy(cname, arb_amount, csell[1])
            print "Bought on C, Sold on B"
            print str(datetime.datetime.now())
            print str(csell) + " Bought Price"
            print str(bbuy) + " Sell Price"
        else:
            print "Size limits, would have Bought on C, sold on B"
            print str(datetime.datetime.now())
            print str(csell) + " Bought Price"
            print str(bbuy) + " Sell Price"
    elif bsell[1]*(1+thresh)<cbuy[1]:    #Buy on Bter, sell on Cryptsy
        max_sell = cryptsy_balance(curr)
        if max_sell>arb_amount and min(cbuy[0],bsell[0])>arb_amount*1.5:
            bter_exchange.placeOrder(pair, 'buy', cbuy[1], arb_amount)
            exchange.sell(cname, arb_amount, bsell[1])
            print "Bought on B, Sold on C"
            print str(datetime.datetime.now())
            print str(cbuy) + " Sell Price"
            print str(bsell) +  " Bought Price"
        else:
            print "Size limits, would have Bought on B, sold on C"
            print str(datetime.datetime.now())
            print str(cbuy) + " Sell Price"
            print str(bsell) +  " Bought Price"
    else:
        print "No Arb"
        print str(datetime.datetime.now())
    print "One Round down"

{% endhighlight %}

Definitely an interesting learning experience! A lot of fees crop up, and without operating at scale, it doesn't work too well. However, again, it still netted me a nice meal!

Soon after BTC's peak, a new currency started gaining traction: Litecoin - similar concept but a different hashing algorithm. I decided build a mining rig. Five graphics cards later - I had a barebones mining rig that could just about cover the cost of electricity every month! The one upside to running this machine all night was it gave off just enough heat for me to forgo my heater in the small studio apartment I lived in.

GPUs soon gave way to ASICs - and I was one of the first in line to buy a proper mining rig! We ran this rig for nearly 2 years - definitely cash flow positive, but again, just another nice dinner.

Today:

With Bitcoin in the limelight, and not just as a currency, there is a lot of work being done towards propogating the fundamental ideas of cryptocurrencies to greater use. I'm excited to see where we end up in 5 to 10 years time.



