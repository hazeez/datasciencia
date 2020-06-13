---
title: "How To Use Checklists - Post 11"
date: 2019-10-30T10:07:47+06:00
draft: false

# post thumb
image: "images/post/marcin-jozwiak-l5plFZq7E28-unsplash.jpg"
image_credit: "Photo by Marcin Jozwiak on Unsplash"


# meta description
description: "this is meta description"

# taxonomies
categories: 
  - "Go Language"
tags:
  - "Photos"
  - "Game"
  - "HTML"
  - "Python"
  - "New"

# post type
type: "post"
---

# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6


{{<codeblock filename="test.py">}}
```python
print("Hello, world!")
print("Hello, world!")
print("Hello, world!")
print("Hello, world!")
s = "Python syntax highlighting"
print s
```
{{</codeblock>}}

{{<customtable tablename="Table 1">}}
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
{{</customtable>}}

##### Emphasis

Emphasis, aka italics, with *asterisks* or _underscores_.

Strong emphasis, aka bold, with **asterisks** or __underscores__.

Combined emphasis with **asterisks and _underscores_**.

Strikethrough uses two tildes. ~~Scratch this.~~

<hr>

##### Link
[I'm an inline-style link](https://www.google.com)

[I'm an inline-style link with title](https://www.google.com "Google's Homepage")

[I'm a reference-style link][Arbitrary case-insensitive reference text]

[I'm a relative reference to a repository file](../blob/master/LICENSE)

[You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself].

URLs and URLs in angle brackets will automatically get turned into links. 
http://www.example.com or <http://www.example.com> and sometimes 
example.com (but not on Github, for example).

Some text to show that the reference links can follow later.

[arbitrary case-insensitive reference text]: https://www.mozilla.org
[1]: http://slashdot.org
[link text itself]: http://www.reddit.com

<hr>

##### Paragraph

Lorem ipsum dolor sit amet consectetur adipisicing elit. Quam nihil enim maxime corporis cumque totam aliquid nam sint inventore optio modi neque laborum officiis necessitatibus, facilis placeat pariatur! Voluptatem, sed harum pariatur adipisci voluptates voluptatum cumque, porro sint minima similique magni perferendis fuga! Optio vel ipsum excepturi tempore reiciendis id quidem? Vel in, doloribus debitis nesciunt fugit sequi magnam accusantium modi neque quis, vitae velit, pariatur harum autem a! Velit impedit atque maiores animi possimus asperiores natus repellendus excepturi sint architecto eligendi non, omnis nihil. Facilis, doloremque illum. Fugit optio laborum minus debitis natus illo perspiciatis corporis voluptatum rerum laboriosam.

<hr>

##### List

1. List item
2. List item
3. List item
4. List item
5. List item

##### Unordered List

* List item
* List item
* List item
* List item
* List item

<hr>

##### Code and Syntax Highlighting

Inline `code` has `back-ticks around` it.

```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```
 
```python
s = "Python syntax highlighting"
print s
```
 
```html
No language indicated, so no syntax highlighting. 
But let's throw in a <b>tag</b>.
```

{{< highlight python "linenos=table,hl_lines=1,  linenostart=1" >}}
'''filename.py'''
s = "Python syntax highlighting"
print s
{{< /highlight >}}


##### Blockquote

> This is a blockquote example.

<hr>

##### Inline HTML

You can also use raw HTML in your Markdown, and it'll mostly work pretty well.

<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>


<hr>

##### Tables

Colons can be used to align columns.

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

There must be at least 3 dashes separating each header cell.
The outer pipes (|) are optional, and you don't need to make the 
raw Markdown line up prettily. You can also use inline Markdown.

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3

<hr>

##### Image

![image](../../images/post/post-1.jpg)
![image](../../images/post/juan-davila-P8PlK2nGwqA-unsplash.jpg)
![image](../../images/post/jay-mantri-TFyi0QOx08c-unsplash.jpg) 
<hr>

##### Youtube video

{{< youtube C0DPdy98e4c >}}

{{<figure src="https://res.cloudinary.com/datasciencia/image/upload/v1590855708/Greenshot/2020_05_30_21_51_39_Window_xoba2q.png" caption="cloudinary image" link="https://res.cloudinary.com/datasciencia/image/upload/v1590855708/Greenshot/2020_05_30_21_51_39_Window_xoba2q.png" target="https://res.cloudinary.com/datasciencia/image/upload/v1590855708/Greenshot/2020_05_30_21_51_39_Window_xoba2q.png">}}

{{<codeblock filename="flask-d3-socketio.py">}}
```python
from flask import Flask, render_template, jsonify
from flask_socketio import SocketIO, emit
import json

app = Flask(__name__)
socketio = SocketIO(app)
app.config['SECRET_KEY'] = '!secret'

# List all the unique users in the chat
list_chat_users = []

# message data dictionary
message_data = {'user': {}}

# message user list
# empty list to store all the chat metrics
msg_data_list = []

# set the color for each user - for d3 to fill a circle for a user
colors = ["blue", "pink", "red", "orange", "green"]

# set the user count to 0
user_count = 0

# set the total message count to 0
total_messages = 0


# class to assign a user and the message
class ChatData:
    # constructor
    def __init__(self, number, name, message_count, user_color):
        self.number = number
        self.name = name
        self.message_count = message_count
        self.color = user_color


@app.route('/')
def index():
    return render_template('index.html')


# execute this when the client establishes a connection
@socketio.on('connect', namespace='/test')
def test_connect():
    emit('my_response', {'data': 'Connected'})


@socketio.on('my_broadcast_event', namespace='/test')
def broadcast_message(message):
    # check the message payload and if the users is not in list_chat_users
    # then add them to the list
    global list_chat_users
    global message_data
    global msg_data_list
    global user_count
    global total_messages

    # get the user from the message from the client
    chat_user = message['data']['user']

    # if the user is not a part of of the list then add him / her to the list
    if chat_user not in list_chat_users:
        # increment the user by 1
        user_count += 1
        total_messages += 1

        # add them to the user list
        list_chat_users.append(chat_user)

        # Instantiate a user and the message count to 1 at the first message
        # from the user
        user = ChatData(user_count, chat_user, 1, colors[user_count - 1])

        # creating a dictionary in the form of
        # e.g. {'user':{'num':1, 'name':'Azeez', 'msg_count':1, "color":blue}}

        message_data['user']['num'] = user.number
        message_data['user']['name'] = user.name
        message_data['user']['msg_count'] = user.message_count
        message_data['user']['color'] = user.color

        # add it to the msg_data_list
        msg_data_list.append(message_data)
        # reset the nested dictionary
        message_data = {'user': {}}
        print msg_data_list

    else:
        # if the user already has sent the message and is in the list chat users
        # increment the total messages by 1
        total_messages += 1
        # update the message count for the user by 1
        # iterate thru the list of dictionaries
        for dict_items in msg_data_list:
            # iterate thru the dictionary
            for key, value in dict_items['user'].iteritems():
                # increment the msg count by 1 for the user who sends a message
                if dict_items['user']['name'] == chat_user:
                    dict_items['user']['msg_count'] += 1
                    print msg_data_list
                # if the msg count is incremented by 1, break the loop
                # as we don't have to loop thru the rest of the dictionary
                break

    # send the chat message back to the client and send the chat metrics data
    emit('my_response', {'data': message['data'], 'd3_data': msg_data_list,
                         'total_messages': total_messages}, broadcast=True)


@socketio.on('my_circle_event', namespace="/test")
def broadcast_click_event(message):
    emit('my_circle_response', {'data' : message}, broadcast=True)


if __name__ == '__main__':
    socketio.run(app, debug=True)
```
{{</codeblock>}}
