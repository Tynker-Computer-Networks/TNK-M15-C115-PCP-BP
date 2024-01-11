TAMBOLA STAGE - 3
======================
In this activity, you will mark the number on the tambola and label it.
<img src= "https://media.slid.es/uploads/1525744/images/8813171/prjct.png" width = "100%" height = "50%">




Follow the given steps to complete this activity.




1. Mark the Number
* Open the file `client.py`.
* Define a function to mark a number using button text, configure the color on marking it.
```
def mark_number(button):
    global marked_number_list, flash_number_list, current_number_list, gameOver, flash_number_label, canvas2, player_name, SERVER
    button_text = int(button['text'])
    marked_number_list.append(button_text)
    button.configure(state='disabled',background='#c5e1a5', foreground="black")
```


* Configure the box_button to run the mark_number() function when clicked using the command parameter.
    box_button.configure(command = lambda box_button=box_button :mark_number(box_button))
* Configure the background color for the previous position.


* Create an infinite loop to flash the number on the label.
```
while True:
    chunk = SERVER.recv(2048).decode()
    if(chunk in numbers and flash_number_label):
        flash_number_list.append(int(chunk))
        canvas2.itemconfigure(flash_number_label, text = chunk, font = ('Chalkboard SE', 60))
```
* Create and start a thread to receive the message.
```
thread = Thread(target=receive_msg)
thread.start()
```


* Save and run the code by first running the server.py and then client.py to check the output.
