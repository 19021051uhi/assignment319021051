Video link: # https://youtu.be/tT9EIjbTA8w

# Introduction

The concept is to implement a few new features to an existing project to
make it more useful and user-friendly. The main project is based on the
<https://i-want-to-study-engineering.org/q/balances> website.

![](https://github.com/19021051uhi/assignment319021051/blob/main/Picture1.png)

We are meant to deliver three kinds of new features to the project which
are consist of:

1)  Live chat support

2)  Any reported issues that are non-repeating (from live chat) shown as
    FAQ’s.

3)  Give hinting using an overall percentage of responses for each
    answer.

In this term, the user will be able to get in touch with the admins and
get support whenever it is needed. There are different places that the
user can submit a question and get a reply for that particular problem.
On the other hand, when admins feel that a user’s question would be
beneficial to the others, they can add to the FAQs by selecting a part
of their chat history.

There is also the ‘Hints’ feature that the user can use to see the
percentage of the submitted answers for a multi-choice question by the
other users.

# Methodology

This is the final look of the website. Different features have been
developed which will be described in the following:

![](https://github.com/19021051uhi/assignment319021051/blob/main/Picture2.png)

## Google Authentication

Firebase Google Authentication flow has been used to sign in/signup the
user. The user will be prompted to login using a Google account and will
be taken to the home page once signed in.

![](https://github.com/19021051uhi/assignment319021051/blob/main/Picture3.png)

## Question submission

Once the user submits a new question, the app will check if the user has
been already registered with the Google Firestore or not, and if not,
the app will complete the user’s info. In the next step, the app will
create a new document with the user’s info and the info regarding the
live chat support which will be explained in the next section. The
system will print an appropriate message to the user after successful
submission.

![](https://github.com/19021051uhi/assignment319021051/blob/main/Picture4.png)

## Live chat support

As it is visible in the screenshot below, a notification will be shown
to the admin once there is a new question available to review.

![](https://github.com/19021051uhi/assignment319021051/blob/main/Picture5.png)

After clicking on the notification, a pop-up chat window will open to
reply to the user. Admins can upload media using the camera icon
provided.

![](https://github.com/19021051uhi/assignment319021051/blob/main/Picture6.png)

Back to the user’s dashboard, and once an admin replies to the user’s
question, an ‘R’ notification will be shown to the user and by clicking
on it, the user can access the live chat support. From now on, the
conversation can be moved forward by tapping on the notification by
either side.

![](https://github.com/19021051uhi/assignment319021051/blob/main/Picture7.png)

## FAQs

In the previous section, if an admin decides to add a reply to the FAQs,
the selected answer will be listed and shown next to the questions
pop-up video. The overflowed FAQs can be scrolled down to maintain the
pop-up screen dimensions and layout.

![](https://github.com/19021051uhi/assignment319021051/blob/main/Picture8.png)

## Hints

This part is the hints implementation where the user can see the
calculated percentage of each answer selected by all users. I have
enabled a user to be able to submit unlimited answers to test the Hints
functionality. This is a real-time feature that will be demonstrated in
the video provided for this coursework.

![](https://github.com/19021051uhi/assignment319021051/blob/main/Picture9.png)

If we press the “CHECK MY ANSWER” button, we will dig through the
‘balance’ question JSON file to get the correct answer and check
against the user selection. I needed to update all answers button type
when selecting an answer.

# Evaluation

Generally, all features have been implemented in the app and working
correctly. All client requirements have been met. There were a couple of
instances that I had to simplify the process to be able to demonstrate
the feature. I came with the idea to create different data collection
for each functionality within the app but with the fact that they all
need to be accessible for different purposes. Hence, I have created a
**user** collection to store simple user’s data i.e. email, name and
role.

I decided not to add a user automatically once logged in using the
Google authentication. Instead, I will register the user’s details as
soon as submitting a new question. First check if the user exists and
then create a \`Chat\` collection with the user’s id, photo, text and
uploaded file link (if there’s any).

![](https://github.com/19021051uhi/assignment319021051/blob/main/Picture10.png)

The other challenge was to show an appropriate notifications layout for
an admin or a simple user above the page. What I have done is that
before displaying anything, I will do a few simple Firestore queries to
check whether the user is admin and if so, whether there is an unread
new message received or not. On the other hand, if it is a simple user
and already submitted a question and waiting for a reply, has an
\`adminid\` been assigned to the question or not.

Actually, when an admin replies to a user question, we will update the
‘adminid\` field of that question with the admin id. Now we can show a
notification to the user that your question has been reviewed.

![](https://github.com/19021051uhi/assignment319021051/blob/main/Picture11.png)

The next challenge was to create a customisable pop-up window within the
React, which I used Modals implement. Along with this, I did some CSS
refactoring in the UI to match the given design. By comparing all the
chat’s \`userid\` and the current \`userid\` I distinguished the
messages and changed the chatbox layout to resemble a normal chat
structure. Also, I had to add the FAQ for the messages that an admin has
sent.

![](https://github.com/19021051uhi/assignment319021051/blob/main/Picture12.png)

Despite all, in my opinion, the most challenging part was to create a
file upload functionality with a custom attach icon. I have added
listeners to save the file’s name and different conditions for sending a
message where there is or is not a file attached with that message.

Apart from these, I had to upload the file using the Firebase storage,
get the link and include the link as one of the message fields.
Conditional document updates were one of those puzzles to solve\!

Showing FAQs within the Modal pop-up window was a time-taking issue. It
was mostly CSS structuring, but with the fact that I needed to switch
between different layouts within a unique UI, meaning that there are
different views when there is or is not a FAQ section next to the
guiding video.

The last part was to work out the correct percentage for each selected
answer based on the number of total users that have answered the
question. Thus, I came up with the idea to create a couple of documents
to save the number of time that a specific answer has been selected,
plus the total number of users. In this term, I will calculate the
percentage for each given answer.

The issue was if I am to select an answer and work out the percentage
for that specific answer, the percentage for each individual answer will
not add up to 100. So, I had to update all the other rows as well in
real-time to make this happen.

Finally, I am happy with the final output. The entire project went
smoothly to the end but there were a few instances that needed more
complicated workaround to get the process done. The app based on the
fact that there is only a balance question to be dealt with but
generally I have designed the app to be able to change the static
content with dynamic content coming from an API endpoint.

![](https://github.com/19021051uhi/assignment319021051/blob/main/Picture13.png)
