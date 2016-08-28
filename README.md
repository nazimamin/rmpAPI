# RateSBU
Chrome Extension: Professor's rating from Rate My Professor's site in Solar

---

A chrome extension that queries professors' ratings from Rate My Professors's website and shows inside Stony Brook University's class management tool (Solar). 

##Extention [RateSBU][3] -- [Code][4]



Backend [https://ratesbu.herokuapp.com/][1] parses html from  [http://www.ratemyprofessors.com/][2] and returns as JSON

##Example POST request##
```javasript
         {
         "school": "Stony Brook University",
         "comments": false,
         "prof": [{
                  "names": ["Paul Fodor"]
          }]
         }
```
####or####
```javasript
        {
        "school": "ANY SCHOOL NAME",
        "comments": true,
        "prof": [{
            "id": "CAN BE BLANK",
            "names": ["Paul Fodor", "Chelsea Kennedy"]
        }]
    }
    ```
####or####
```javasript
    {
         "school": "Stony Brook University",
        "comments": false,
        "prof": [{
            "id": "MTG_INSTR$0",
            "names": ["Paul Fodor"]
        }, { 
            "id": "MTG_INSTR$0",
            "names": ["Chelsea Kennedy"]
        }]
    }

```

##Example Response##
 
 Response with "false" flag
 ```javasript
 ---
      {
    "prof": [
        {
            "id": "SOME ID OR NOT",
            "name": "Paul Fodor",
            "pid": "1614881",
            "quality": [
                {
                    "OverallQuality": "4.6",
                    "Clarity": "4.5",
                    "AverageGrade": "A-",
                    "Helpfulness": "4.7",
                    "Easiness": "3.5",
                    "Hotness": "http://www.ratemyprofessors.com/assets/chilis/scorching-chili.png"
                }
            ]
        }
    ]
    }
  ```  
 Response with "true" flag
  ```javasript   
  ---
    {
    "prof": [
        {
            "id": "MTG_INSTR\\$0",
            "name": "Paul Fodor",
            "pid": "1614881",
            "quality": [
                {
                    "OverallQuality": "4.6",
                    "Clarity": "4.5",
                    "AverageGrade": "A-",
                    "Helpfulness": "4.7",
                    "Easiness": "3.5",
                    "Hotness": "http://www.ratemyprofessors.com/assets/chilis/scorching-chili.png"
                },
                {
                    "comments": [
                        {
                            "date": "03/10/2015",
                            "class": "CSE 114",
                            "comment": "Fodor has been one of the best professor I had in Stony. Although the class was around 8AM, I was there most of the time because his lectures we informative and easy to follow. He helps you out a lot and his office hours are usually packed with students. Before a test, learn all the functions he expects of you and you will be fine."
                        }{
                           -- MORE COMMENTS..
                        }
                    ]
                }
            ]
        },
        {
            "id": "MTG_INSTR\\$0",
            "name": "Chelsea Kennedy",
            "pid": "2009132",
            "quality": [
                {
                    "OverallQuality": "4.0",
                    "Clarity": "4.0",
                    "AverageGrade": "N/A",
                    "Helpfulness": "4.0",
                    "Easiness": "3.0",
                    "Hotness": "http://www.ratemyprofessors.com/assets/chilis/cold-chili.png"
                },
                {
                    "comments": [
                        {
                            "date": "05/02/2015",
                            "class": "AMS 102",
                            "comment": "She's really helpful and really clear in teaching and she's willing to stop the lecture to make sure everyone understands the concepts. She's available for help often and makes contact with students to make sure everyone knows what's going on. She is a bit of a tough grader, though and there's plenty of homework."
                        }
                    ]
                }
            ]
        }
    ]
}
```

  [1]: https://ratesbu.herokuapp.com/
  [2]: http://www.ratemyprofessors.com/
  [3]: https://goo.gl/LEA2fv
  [4]: https://github.com/NazimAmin/RateSBU/tree/master/RateSBU-extension

