## App Concept
- App is a toolbox for anyone who wants to research what stocks to buy in the stock market
    - Many apps to assist with stock-picking exist like this one today, but this one will have more character by lightly nudging a user towards a time-tested approach to stock-picking called "value-investing"
    - Will be almost entirely quantitative with a major focus on how any given company in the stock market has historically behaved based on its financial statements. 
    - The only qualitative bits of information are description of how a company makes its money and its industry
        - This description will be derived from the business summary section of the company's most recent 10-K

## Theme
- Theme is mostly grayscale and blue with a black navbar
- I wanted a relatively simple scheme that was also dark because I prefer reading light text on a dark background

 ## Layout   
- App's title at left of navbar with navbar hyperlinks situated to the title's right
    - Profile component of navbar is a collapsible menu button so that:
        - 1) A user definitely sees it compared to the rest of the nav-bar hyperlinks
        - 2) It doesn't take up unnecessary space in the navbar if a user doesn't want to log in
![general page layout](/planning/wireframes/expanded-menu.png)
![general page layout](/planning/wireframes/collapsed.png)
- Navbar items (each of which color blue on hovering):
    - Stockpile (just a title, no functionality)
    - More about our way
        - "We don't look at stocks like some hot commodity to swap back and forth for an adrenaline rush because they've had some crazy price changes lately. A stock is just a slice of the pie, the entire company being the whole pie. So for starters, just remember that any time we're buying a stock we're behaving as though we want to buy the entire business.
        - Now imagine you want to buy a lemonade stand, a business that has to make a profit to stick around. How would you know what a fair price is for that business? You base your decision on how much money it usually makes on any given year. Since some businesses are seasonal, looking at profit numbers on a yearly basis ensures that you will never be overvaluing a summer business (like an ice cream truck) because it's been hot lately or a winter business (like snow-shoveling) because we just had a blizzard.
        - So now the next question you might be asking yourself is , "Ok, well how many years of profit is a business worth?" A good number is 8 times a companies usual profit on any given year. This effective strategy covers you in two ways. By default you won't be buying into companies that haven't actually been making money. You also won't get reamed by somebody trying to get you to overpay for their business.
        - This last part is the icing on the cake (or pie, or whatever). What if you have 20 lemonade stands all willing to sell you their entire company for less than 8 years of their profits and you could only afford to buy 5 of them? Well, you just pick the top 5 that give you the most bang for your buck. More specifically, buy the 5 giving you the most profit for every dollar you pay. This process of buying 5 profitable companies that are all on sale for a great price is what's called "diversification". Basically, if one of the companies has a run of bad luck you still got 4 great ones to more than cover you.
        - We hope you enjoy using the tools in Stockpile to help you find those 5 great businesses to build your financial future on. Happy hunting.
        - Casey Jones"
        ![](/planning/wireframes/our-way.png)
    - My Stocks
        - Each stock shows up as a bootstrapped card with the name of a company, a short decription of a company, a button that says "View" which will submit a put request for a "show-stock" (show-stock.liquid) page, a delete button, the price of the stock the last time you viewed it, and our recommendation for the appropriate buy price when a user added it to the my-stocks page
        ![](/planning/wireframes/my-stocks.png)
        - Show page includes a wealth of data (also accessed by the "Search Any Stock" navbar link and searching the stock):
            - Button for "Remove From My Stocks" in the upper-right-hand corner of the screen
            - Stock's name and ticker
            - Unordered list of which appear from a user standpoint to be key: value pairs pulled from the company's most recent 10-Q (quarterly report), including but not limited to (STRETCH GOAL: hovering over 'keys' will show an info box describing the metric you are hovering over, since I can't even remember what all these metrics mean or how they are calculated all the time):
                - Description (more thorough than on "My Stocks" but still pulled from company's most recent 10-K): [string]
                - Last close: [number]
                - Market Capitalization : [number]
                - Trading Volume After Last Close: [number]
                - Dividend Yield [number]
                - Earnings Per Share: [number]
                - Price To Earnings Ratio: [number]
                - Free Cash Flow Per Share: [number]
                - Price to FCF Ratio: [number]
                - etc....
            - A table with three hyperlinks at the top (maybe built into the top row of the table to look like a navbar?) saying "Income Statement", "Balance Sheet", and "Cash Flow Statement"
                - This one table is the meat and potatoes of the entire app to me
                - This table can switch between viewing a company's Income Statement (selected when opening show page by default), Balance Sheet, or Cash Flow Statement by switching on each different hyperlink in the top row of the table
                - The second row of the table will be a list of column headers to show the last 10 years of annual reports from (left to right) oldest to newest with 6 additional columns appended to the end of the most recent year's row displaying headers of (again, left to right):
                    - 1) Last 12 Months (compiled using a company's last 4 10-Qs or 'quarterly reports')
                        - Important that the last 12 months of a company's reported numbers are relatively in-line with the last annual report or 10-K's numbers
                        - If they are not, that alludes to a company possibly sprucing up their annual reports too much
                    - 2) 10YrCAGR (Compounded Annual Growth Rate)
                    - 3) 8YrCAGR
                    - 4) 6YrCAGR
                    - 5) 4YrCAGR
                    - 6) 2YrCAGR
                - Second row and every row after it will have a total of 16 columns, and 
                    - Some rows may have data like company expenses be negative which is totally ok, don't know if I want to color them red yet since I don't want anyone to think "danger" just because a company has expenses
                ![](/planning/wireframes/show-page.png)
    - My Portfolios
        - Looks like the my-stocks page just without the logo present on each individual stock on my-stocks page
        ![](/planning/wireframes/my-portfolios.png)
    - Search any stock
        - Will show a search bar upon navigation to page (a form) to enter any company on the stock market's name or ticker (like Apple's ticker is AAPL)
            - STRETCH GOAL: search bar will suggest a stock's ticker and name based on every character a user inputs into the form input
        - Just a text input field and a submit button to go with it
        ![](/planning/wireframes/search-page.png)
        - After entering a stock's name or ticker, you will just go to the same 'show' page detailed above EXCEPT:
            - Button for "Add to My Stocks" in the upper-right-hand corner of the screen is changed to say "Remove From My Stocks" based on whether you already added this stock to your "My Stocks" or not
    - Backtesting
        - Takes the company's listed in "My Stocks" and with a form with just 2 inputs, shows how your stocks would have done between the dates specified in each input field
        ![](/planning/wireframes/backtesting-page.png)
    - [login status]
        - if not logged in, will show "Log In" followed by "Sign Up" to give new users a chance to sign up and give old users a chance to log back in
        - if logged in, will show the user's username followed by "Log Out"
- More stretch goals:
    - Have a backtesting page to backtest any given portfolio or stock over time
    - Have a stock price chart provide a render animation over the backtesting time period selected

## Entity Relationship Diagram
![](/planning/wireframes/erd.png)

## User Stories

1. User navigates to our-way page to see how we view stocks
2. User uses navbar at top to get to most pages
3. User can navigate to portfolio show page to add a stock to a portfolio
4. User can navigate to portfolio show page to remove a stock from a portfolio
5. User can view into on an individual stock to check last stock price
6. User can view table of company's financial records to evaluate company
7. User can edit and update their portfolios over time using edit button inside each portfolio's card on the index page
8. User can infer the market capitalization of any stock by multiplying the recent share price by the number of shares (shown in the top row of the stock show-page table) to see how much it would cost to buy the whole company
9. User can educate themselves on how to generally value a company by reading our-way page
10. User can make multiple portfolios to group their stocks by industry or sub-industry
11. User can view a stock's cash flow ratios to compare two stocks to each other to see which one is more valuable at the moment using each individual stock's show page accessed from the stock-index page
12. User can sign up and log in to pick up editing their portfolios or their stocks where they left off
13. User doesn't have to log in and can just view metrics on any stock on the market, and even add it to a my-stocks page without being logged in (resulting in a social network of sorts when many users get involved)
14. User can delete any stock that is no longer listed on the market
15. User can see a company's profits on any given year in the last decade to evaluate a company's earnings growth over time

## Route Table

|   NAME   |     PATH       |   HTTP VERB     |            PURPOSE                   |
|----------|----------------|-----------------|--------------------------------------| 
| Index    | /title/our-way      |       GET       | Displays our-way page           |
| New      | /title/my-portfolios/new |       GET       | Shows form for new portfolio creation |
| Show     | /title/my-portfolios |       GET       | Shows my portfolios             |
| Show     | /title/my-stocks    |     GET         | Shows my stocks                 |
| Show     | /title/my-portfolios/:id |       GET        | Shows one portfolio from my-portfolios |
| Show     | /title/my-stocks/:id |       GET       | Shows one stock from my-stocks or from an individual portfolio |
| Show     | /title/backtesting |       GET         | Shows backtesting page          |
| Edit     | /title/my-portfolios/:id/edit |       GET        | Shows edit page for one portfolio where you can add or delete stocks from a portfolio |
| Create   | /title/my-stocks    |      POST       | Adds a new stock to the my-stocks page from the search-stocks page |
| Create   | /title/my-portfolios |      POST       | Adds a new portfolio to the my-portfolios page from the my-portfolios/new page |
| Destroy  | /title/my-portfolios/:id |      DELETE     | Deletes an entire portfolio |
| Destroy  | /title/my-stocks/:id |     DELETE      | Deletes a stock from my-stocks |
| Update   | /title/my-portfolios/:id |      PUT        | Adds or removes a stock from a single portfolio |