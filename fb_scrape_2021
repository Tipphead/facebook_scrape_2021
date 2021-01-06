# -*- coding: utf-8 -*-
"""
Created on Wed Dec 23 18:23:54 2020

@author: j
"""

from bs4 import BeautifulSoup
import pandas
import time
from selenium import webdriver

user_name = ''
password = ''
page_to_scrape = '' 




def _expand_comment(browser):
    #scrape comments of comments of comments of comments of...
    #expandables = browser.find_elements_by_class_name("async_elem")
    #expand all comments of comments
    i = 0
    while (True):
        try:
            browser.find_elements_by_class_name("async_elem")[i].click()
            time.sleep(4)
        except:
            i+=1
            break
def _find_posts(browser, numOfPost):
        elements = browser.find_elements_by_xpath("//a[contains(@class,'_15kq _77li')]")
        comment_list = []
        date_list = []
        #expand page with view more comments button
        
        #find posts        
        while (numOfPost > len(elements)):
            try:
                elements[-1].click()
            except:
                print("Cannot comment (click) on post id: " + elements[-1].id)
            browser.back()
            time.sleep(1)
            elements = browser.find_elements_by_xpath("//a[contains(@class,'_15kq _77li')]")
        #scrape comments and date of post
        for i in range(numOfPost):
            #finds 'Comment' button on post
            elements = browser.find_elements_by_xpath("//a[contains(@class,'_15kq _77li')]")
            try:
                elements[i].click()
                time.sleep(1)
                _expand_comment(browser)
                soup1 = BeautifulSoup(browser.page_source, "html.parser")
            except:
                print("Post " + elements[i].id + ": No comments1")
                continue
            #finds date of post in page source url
            try:
                date_list.append(soup1.find('abbr').text)
            except:
                time.sleep(1)
                elements = browser.find_elements_by_xpath("//a[contains(@class,'_15kq _77li')]")
                elements[i].click()
                time.sleep(1)
                soup1 = BeautifulSoup(browser.page_source, "html.parser")
                print("Date problem: ", i)
            #finds comments in page source url
            try:
                comment_list.append([item.text for item in soup1.select("[data-sigil='comment-body']")])
            except:
                print("Post ", i, ": No comments2")
            #began organizing comments within comments
            for i in range(len(soup1.select("[data-sigil='comment-body']"))):
                try:
                    if (soup1.select("[data-sigil='comment-body']")[i].find('a').name == 'a'):
                        comment_list[0][i] = comment_list[0][i].replace(comment_list[0][i], i, + comment_list[0][i])
                except:
                    continue
            if (browser.current_url != "https://m.facebook.com/" + page_to_scrape):
                browser.back()
                time.sleep(1)       
            #previously was saving comments and dates in dataframe, switched
            #to lists I was organizing comments within comments
            # df = pandas.DataFrame(columns=['date','comments'])
            # df['date'] = date_list
            # df['comments'] = pandas.Series(comment_list)
            
        return date_list, comment_list
        

def _log_in(user_name, password, page_to_scrape):
    # Step 1) Open Firefox 
    browser = webdriver.Firefox()
    # Step 2) Navigate to Facebook
    browser.get("http://www.facebook.com")
    # Step 3) Search & Enter the Email or Phone field & Enter Password
    username = browser.find_element_by_id("email")
    password = browser.find_element_by_id("pass")
    submit   = browser.find_element_by_id("u_0_b")
    username.send_keys(user_name)
    password.send_keys(password)
    # Step 4) Click Login
    submit.click()
    browser.get('https://m.facebook.com/' + page_to_scrape)
    browser.maximize_window()
    return browser





