# Python Refresher

## Back to basics

=== "Variables"

    ```py
    two = 2
    some_number = 10000

    # Booleans
    true_boolean = True
    false_boolean = False

    # String
    my_name = "This is a string"

    # Float
    book_price = 15.80
    ```

=== "Control Flow"

    ```py
    if 2 > 1:
        print("2 is greater than 1")
    elif:
        print("1 is not greater than 2")
    else:
        print("1 is equal to 2")
    ```

=== "Loops"

    ```py
    # While :
    loop_condition = True

    while loop_condition:
        print("Loop Condition keeps: %s" %(loop_condition))
        loop_condition = False

    
    # For :
    for i in range(1, 11):
        print(i)

    for item in list:
        print(item)
    ```

=== "Lists"

    ```py
    programming_languages = ["Python", "C", "Rust", "Java", "Go"]
    # Index are like this :     0       1     2       3      4
    
    print(programming_languages[2])             # Displays "Rust"


    # Let's add some variables to the list
    programming_languages.append("JavaScript")  # Adds JS to the list above
    one_more = "Kotlin"                         
    programming_languages.append(one_more)      # Adds Kotlin to the list
    
    print(programming_languages[6])             # Displays "Kotlin"
    ```

=== "Dictionaries"

    ```py
    dictionary_example = {
        "key1": "value1",
        "key2": 2,
        3: "val3"
    }

    print("The first value is %s" %(dictionary_example["key1"]))    
            # Displays value of key1
    print("The second value is " + str(dictionary_example["key2"])) 
                # Displays value of key2
    print("The second value is " + dictionary_example[3])           
            # Displays value of key3

    dictionary_example['keyFour'] = "v4"                            
            # Adds keyFour as the 4th key, with value or "v4"
    print(dictionary_example)                                       
            # Displays whole dictionary

    # Display dictionary :
    for key, value in dictionary.items():
        print("%s takes the value %s" %(key, value)) 
            # key_n takes the value value_n


    ```