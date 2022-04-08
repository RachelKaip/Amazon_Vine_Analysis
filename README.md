# Amazon Vine Review Analysis
## Overview
On Amazon, there are two tiers of reviewers, a general customer or a "Vine Voice".  General custoemrs are just that- someone who bought the product and decided to log in a and leave a review.  However, while Vine Voices were once general customers too, they are now part of an invitation-only group who receive gifts and free products from Amazon to review on the site. 

The purpose of this analysis is to determine if there may or may not be a positivity bias in Vine reviews for home products due to their exclusive position.  

**Tools Used:**
- AWS RDS 
- PySpark
- PostgreSQL

## Results 
I started the analysis by inserting all of the reviews into a PySpark dataframe and filtering for products with 20 or more reviews.  Then, I filtered through the products with 20 or more reviews to find what I've determined to be "helpful reviews". I did this by looking for products with a 50% helpfullness rate or higher after dividing each products helpful_votes by it's total_votes.  This left us with 92,216 reviews to analyze.    

##### Total Reviews 
From the helpful_reviews dataframe, I then filtered and spereated the Vine and non-Vine reviews.  There were 1,448 and 90, 768 reviews respectively.  Please see my method below:    

![totalpaid](https://user-images.githubusercontent.com/94569240/162432491-bf60254b-81d6-48a3-8561-91663dc399b2.PNG)


![totalunpaid](https://user-images.githubusercontent.com/94569240/162432508-b1c744d6-7faa-468b-8f41-033a4ffd5103.PNG)


##### 5 Star Reviews 
Within each dataframe, Vine and non-Vine, I filtered to count only 5 star reviews.  

There were 647 5 star Vine reviews- 

![paid5star](https://user-images.githubusercontent.com/94569240/162432544-27b0a2af-c611-40ed-93a1-26ab9a0daf28.PNG)

-and there were 4,4104 5 star non-Vine reviews.  

![unpaid5star](https://user-images.githubusercontent.com/94569240/162432562-47f16f0c-fb86-4fd8-806a-cd0c7480fb47.PNG)


##### Percentage of 5 Star Reviews
Lastly, using the numbers calculated above,  I found the percent of 5 star reviews by dividing the total 5-star reviews by the total reviews for each population.

The Vine Voices leave 5-star reviews 44.68% of the time- 

![paidpercent5star](https://user-images.githubusercontent.com/94569240/162432604-45eaa657-ec09-4268-a187-f451a6ba96f0.PNG)

-while Amazon's general customers leave 5 star reviews 48.59% of the time.  

![unpaidpercent5star](https://user-images.githubusercontent.com/94569240/162432626-bd74c260-fbe6-44f8-9d06-81b06c46ed3b.PNG)

## Summary 
Based on my findings, there are two reasons I cannot confidently say there is a positivity bias amongst Amazon's Vine Voice reviewers.  First, the difference in the likelihood of a general customer leavinga  5-star review and a that of a compensated Vine Voicer is only 4%.  This is not a large enough margin to determine any sort of extreme bias.  Secondly, the general customers are the ones most likely to leave a 5-star review!   

I'm happy to report that I beleive Amazon's mission to "[...] increase the availability of customer reviews on newly launched products" for the Vine program is true.  

To take this analysis one step further, I reccomend recoutning these steps for multiple categories and then comparing the results.  Just because the Vine Voicers in the Home category might not be biased, I do not know it's the same in another.  

From there, one could also test to see the likelihood of individual Vine Voicers giving 5 star reviews based on how many reviews they've given and how many of those received perfect scores.  
