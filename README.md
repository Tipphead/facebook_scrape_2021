# koobecaf
## This is a project I began to learn more about Facebook...and GitHub (I clearly don't know the syntax of GH yet!)  It is messy, incomplete and lacking features.  However, it should be a good starting point for someone to learn how to build their own.

# Things this project can do:
 * Mobile Facebook webpage login
 * Navigate to specific Facebook page
 * Find a determined number of posts on a specific Facebook page
 * Scrape date of specific post
 * Scrape text of comments
 * Scrape text of comments of comments
  
# Things this project can*not* do
 * Scrape actual post text
 * Scrape dates of comments
 * Scrape comments beyond ~85 (There is a 'View More Comments' button that must be clicked)

# Methods
### _log_in(user_name, password, page_to_scrape):
 * Method to login to Facebook
 * Provide YOUR user name and password
 * Provide the page you would like to scrape
### _find_posts(browser, numOfPost):
 * Method to find posts of the page you have provided in previous method
### _expand_comment(browser):
 * Expands comments within comments
 
## Feel free to modify the code to your will!  In order to have the program run from the start, I would suggest:
 * variable1 = _log_in(user_name, password, page_to_scrape)
 variable1 would be your browser/driver
 * list1, list2 = _find_posts(browser, numOfPost)
 list1 would be the list to contain dates of posts/list2 would be the list to contain comments
 
 
 
# ONE FINAL THOUGHT:
 * It is my understanding that it is against Facebook Terms of Service to scrape data on users without their consent.  That is why I did not focus on saving user names.  Also, the post text was not scraped because for my particular project, it was not information that I was seeking.  If you have any questions, feel free to comment here and I will do my best to assist you.  This code works with Facebook as of 1/6/2021.


# IF YOU SEE YOUR CODE HERE:
  I apologize for not citing you.  I gathered information from a number of sources.  If you would like to be noted as a contributor, please contact me.

