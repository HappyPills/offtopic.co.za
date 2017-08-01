---
layout: post
title:  "How to Calculate Annualised Growth"
permalink: /finance/how-to-calculate-annualised-growth/
date:   2017-03-06
tags:   finance
categories: finance
---

Ever wanted to know how much your investment has grown on average over the years? Or
perhaps you are considering a specific investment but not sure if it "performs".

You may think that the obvious thing to do would be to fire up Google Finance and
having a look at a very pretty graph showing you that the growth for this investment over the
last 10 years was 150%. Awesome, right?! 150%/10 years is 15% per year which is a really
sweet deal!

If only. No, unfortunately it is a bit more involved than that. The 150% over 10 years
you see is compound growth and the value you are looking for is quite a bit lower than
that... sorry :(

So disappointments aside, how do you calculate annualised growth?

### The Maths
1. Get the starting value of the investment for the period you have select. For ease of
the calculation we'll use the cent value. So let's assume a value of R10,00 which is 1000 cents.

2. Now get the end value for the investment over the period. We'll stick with our example and
use R25,00 which is 2500.

3. Get the "year fractional value" (I made that up for a lack of a better name) which is basically
1 over the amount of years in this period: 1/[years]. So in this example of 10 years it will be 1/10 or 0.1

4. Subtract the starting value from the end value and divide that by the starting value:

    `(2500 - 1000)/1000 = 1.5`

5. Now add 1 to the return rate (step 4) and raise it by the year fractional value (calculated in step 3) and subtract
1 from the result. That might sound confusing but it looks like this:

    `((1.5+1)^0.1)-1`

    Simplified it reads: `(2.5^0.1)-1`  
    Simplified some more: `(1.0959)-1`  
    And the result: `0.0959` *(your annualised growth percentage).*

6. Now multiply the number by 100: `9,59%`

### Let's Recap

Let's use real data - STX40 between 2 Jan 2004 and 30 Dec 2016 (13 years):

Starting value: `960`  
End value: `4382`  
Year fraction: 1/13 = `0.077`

`(4382-960)/960 = 3.56`

`((3.56+1)^0.077)-1 = 0.1239`

Annualised growth: `12.39%`

I know, it feels a bit like high school all over again. That's why I made a [calculator](/finance/tools/annualised-growth-calculator/)
for you to use. You're welcome.
