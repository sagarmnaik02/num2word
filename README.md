# num2word
#The key feature of this module is to when it's imported and written any number, that gets converted to words and this also will give #you the length of all the words of number from 1 till that number.

'''
1. I will first write range of numbers in dict
2. I will manually write 1 to 20 in words in dicti as 1 is key and 'one' is value
3. I will manually write multiples of 10 and 100 in dict as 10 20 30.... 100 200 300... till 1000
'''

num2words = {0:'Zero',
             1:'One',
             2: 'Two',
             3: 'Three',
             4: 'Four',
             5: 'Five',
             6: 'Six',
             7: 'Seven',
             8: 'Eight',
             9: 'Nine',
             10: 'Ten',
             11: 'Eleven',
             12: 'Twelve',
             13: 'Thirteen',
             14: 'Fourteen',
             15: 'Fifeteen',
             16: 'Sixteen',
             17: 'Seventeen',
             18: 'Eighteen',
             19: 'Nineteen',
             20:'Twenty',
             30: 'Thirty',
             40: 'Fourty',
             50: 'Fifty',
             60: 'Sixty',
             70: 'Seventy',
             80: 'Eighty',
             90:'Ninety',
             100: 'Onehundred',
             200: 'Twohundred',
             300:'Threehundred',
             400:'Fourhundred',
             500:'Fivehundred',
             600:'Sixhundred',
             700:'Sevenhundred',
             800:'Eighthundred',
             900:'Ninehundred',
             1000:'Onethousand'
             }

''' now I will use function to call this whenever required
1. I have taken variable Low = length of words and word is equal to 0
2. I have taken a range of 0 to 1000
3. I will take and input in abs value where if the input is negative also it will ignore negative and converts to words
4. if number is more than 1000 then print the msg and break.
5. if user did not give the input in number and gives something else then print msg and take the input again.
6. user given input will go through the loop and gives output of word and length.
7. num2words[num] will give the value of key. this will be concatinated to form words out of number also length will be found.
'''



def num2word(num):
    Low = 0
    word = 0
       
    if  num > 1000:
        print("Sorry Number {} is out of range next time please enter the number in range of 1 to 1000".format(num))
        
    else:
        for num in range(num+1):
            
                                
            if num in num2words:
                word = num2words[num] #this will give the value of the key from dict
                #print("Number to String of {} is:".format(num), word)
                Low += len(num2words[num]) # length of value of key will be found here and added to Low  
                #print("Length of Words: ",Low)
                    
            
            elif num > 20 and num < 100 and num not in num2words:
                word = num2words[num-num%10] + num2words[num%10].lower() #this will give the value of the key from dict
                #(ex : 220- num2words[220-220%10]+num2words[220%10] will give key values as twohundredtwenty from dict)
                #print("Number to String of {} is:".format(num),num2words[num-num%10] + num2words[num%10].lower())
                Low += len(num2words[num-num%10] + num2words[num%10].lower())
                #(ex : 220- Twohundredtwenty length will be found by loop)
                #print("Length of Words: ",Low)
                
            elif num%10 == 0 or ((num//10)%10) == 0:
                word = num2words[num-num%100] + num2words[num%100]
                #print("Number to String of {} is:".format(num),num2words[num-num%100] + num2words[num%100])
                Low += len(num2words[num-num%100] + num2words[num%100].lower())
                #print("Length of Words: ",Low)
                    
            else:
                num > 100 or num < 1001 or num not in num2words
                word = num2words[num-num%100] + num2words[((num%100)//10)*10].lower()  + num2words[num%10].lower() 
                #print("Number to String of {} is:".format(num),num2words[num-num%100] + num2words[((num%100)//10)*10]  + num2words[num%10].lower())
                Low += len(num2words[num-num%100] + num2words[((num%100)//10)*10].lower()  + num2words[num%10].lower())
                #print("Length of Words: ",Low)

    print("Number to String of {} is: ".format(num),word)
    print("Length of Words from one to {}: ".format(word),Low)
    
while True:
    try:
        num = abs(int(input("Enter the number to be converted to the string: ")))
        #taking input as int and abs
        
    except:
        #any input error or key error will be handled here 
        print("Sorry, this is invalid Input, Enter Again: ")
        
        continue
    else:
        break
   
num2word(num)
#lets call for the function here now.
