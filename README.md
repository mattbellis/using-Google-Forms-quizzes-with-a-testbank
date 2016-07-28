# using-Google-Forms-quizzes-with-a-testbank

Here's a quick and dirty way to use the new Google Forms Quizzes with a test bank of your own creation. 

To do this, you'll be running Google Apps Scripts. 

https://developers.google.com/apps-script/

There is a lot of information out there on how to use it, but basically you write a script and save it to Google Drive. You will do the editing and running using 

https://script.google.com

You'll also need to create 3 files (I show you examples of each below)...

* Your test bank (Google Sheets)
* A Google Forms Quiz template (Google Forms)
* A form to pick which questions you want to pull from your test bank for a quiz (Google Sheets)

...and make a copy of my Google Apps Script, modifying it to work with your files. 

Here's some examples of each, formatted in such a way that they will work with the Google Apps Script that I wrote. 

-----
**Test bank**

https://docs.google.com/spreadsheets/d/185vtr8aD-p4NCa5-QyfRJNSba2a1X_yjkkPFF9w66jk/edit?usp=sharing

Note the formatting. This type of formatting is hard coded in the script, but you can see what I'm getting at. 

I've bolded the correct answers, but this is not used when the quiz is created. It's just for the instructor's guidance and you can choose not to do this. 

For "Type", "MC" is multiple choice and "CB" is checkbox, the only two options that Google Quizzes currently takes. 

You can also store images by URL ("Type" = "IU") or stored on your Drive and referenced by ID ("Type" = "ID"). 

-----
**Google Forms Quiz template**

https://docs.google.com/forms/d/1ww-rNPzzr6Jdn3NyqKfo3CqfDofaWGhygFU6BTHyhBk/edit?usp=sharing

Google Apps Scripts does not have features for the Quizzes options, so my workaround is just to make a copy of a quiz template. 

-----
**Quiz maker**

https://docs.google.com/spreadsheets/d/10jBngMHdglLk8TcDGOUTEMbfFCxh1ywAFQ1_E3oxwVQ/edit?usp=sharing

This is the spreadsheet you'll use to make each quiz. You use this to pick the questions you want to use from the test bank and set the title of the quiz. 

-----

Once you have your own versions of these, you'll make a copy of this script

https://script.google.com/d/1rACPT_W6E2u9taMKEIf2IijP6onTUtAyurojSB5di3MCd4deZsgS3KZK/edit?usp=sharing

and edit three places in the beginning, putting in the ID's of your versions of the forms described above. 

From the script...

     /////////////////////////////////////////////////////////////
     // This should be the only things you need to edit for your own use
     /////////////////////////////////////////////////////////////
          
     // These define the ID that you need for your own Google Drive documents. 
     // The ID is a unique identifier for each file. You can grab it from the URL
     // for the document. For instance, if the URL reads...
      //
      //    https://script.google.com/a/siena.edu/d/1rACPT_W6E2u9taMKEIf2IijP6onTUtAyurojSB5di3MCd4deZsgS3KZK/edit?usp=drive_web
      // 
      // then the ID is the string of numbers in the middle
      //
      //    1rACPT_W6E2u9taMKEIf2IijP6onTUtAyurojSB5di3MCd4deZsgS3KZK
      // 
      
      // Here is the Google Sheets that has all your questions.
      var question_bank_ID = '185vtr8aD-p4NCa5-QyfRJNSba2a1X_yjkkPFF9w66jk'
      
      // Here is the Google Sheets that you edit each time you want to select
      // different question numbers from the question bank. 
      var questions_for_quiz_ID = '10jBngMHdglLk8TcDGOUTEMbfFCxh1ywAFQ1_E3oxwVQ'
      
      // Here is the Google Forms Quiz template that will get copied over each
      // time you want to make a new quiz. 
      var quiz_template_ID = '1ww-rNPzzr6Jdn3NyqKfo3CqfDofaWGhygFU6BTHyhBk'
      
      /////////////////////////////////////////////////////////////

If you've added your own file IDs, you can run this script and it will make you a new Google Forms Quiz!

You'll need to add your own answer key and feedback, but this will allow you to reuse questions from one year to the next. 
