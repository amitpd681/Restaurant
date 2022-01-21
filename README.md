class Restaurant:
    
    def __init__(self, name):
        self.restro_name=name
        self.food={}
        self.food_ID=len(self.food)+1
        self.user_details={}
        self.ordered_item=[]

        
    # admin functionalities
               
        
    def add_food_item(self):
        try:
            name=input("Enter the food name : ")
            quantity=float(input("Enter the quantity in values only : "))
            price=float(input("Enter the price in Rs only : "))
            discount=float(input("Enter the discount in Rs only : "))
            stock=float(input("Enter the available stock in values only : "))
            food_item={"Name":name,"Quantity":quantity,"Price":price,"Discount":discount,"Stock":stock}
            self.food_ID=len(self.food)+1
            self.food[self.food_ID]=food_item
            print("\n!! Food Item added successfully !!\n")
            print("Newly Added items :", self.food,"\n")
        except Exception as e:
            print("\n!! Something went wrong please try again !!\n")
        
    def edit_food_item(self):
        try:
            x=int(input("Enter the Food ID you want to update : \n"))
            if x in self.food.keys():
                print("1. Update Food Name\n2. Update Quantity\n3. Update Price\n4. Update Discount\n5. Update Stock \n")
                y= input("Enter the number only : ")
                if y=="1":
                    self.food[x]["Name"]=input("Updated Food name : ")
                    print("\n!! Successfully Updated !!\n")
                elif y=="2":
                    self.food[x]["Quantity"]=float(input("Updated Quantity in values only : "))
                    print("\n!! Successfully Updated !!\n")
                elif y=="3":
                    self.food[x]["Price"]=float(input("Updated Price in Rs only : "))
                    print("\n!! Successfully Updated !!\n")
                elif y=="4":
                    self.food[x]["Discount"]=float(input("Updated Discount in Rs only : "))
                    print("\n!! successfully Updated !!\n")
                elif y=="5":
                    self.food[x]["Stock"]=float(input("Updated Stock in values only : "))
                    print("\n!! Successfully Updated !!\n")
                else:
                    print("!! Sorry Invalid Number !!\n")
            else:
                print("\n!! Incorrect Food ID !!\n")
        except Exception as e:
            print("\n!! Something went wrong please try again !!\n")  
            
    def view_food_item(self):
        print("List of Food Items : \n")
        if len(self.food)!=0:    
            for i in self.food:
                print(f"Food Id : {i}")
                for j in self.food[i]:
                    print(j, ":", self.food[i][j])
                print()
        else:
            print("!! Sorry No Food Items is Added !!\n")

    def delete_food_item(self):
        try:
            print("!! Warning !!\nFood Item will Delete Permanently\n")
            print("Enter the Food ID ")
            x=int(input())
            if x in self.food.keys():
                del self.food[x]
                print("\n!! Food item deleted successfully !!\n")
                print("Updated Food List\n",self.food)
            else:
                print("!! Incorrect Food ID\n !!")
        except Exception as e:
            print("\n!! Something went wrong please try again !!\n")
                
                
    # user functionalities
                   
        
    def user_register(self):
        try:
            user_name=input("Enter your full name : ")
            phone_no=int(input("Enter your 10 digit phone number : "))
            email=input("Enter your email id : ")
            password=input("Enter your password : ")
            address=input("Enter your address with area PIN code ")
            self.user_details={"User Name":user_name,"Phone No.":phone_no,"Email_ID":email,"Password":password,"Address":address}
            print("\n!! Your Account is Created Successfully !!\n")
            print(f"Welcome TO {self.restro_name} Restaurant\n")
            print("User Details : ")
            for i in self.user_details:
                print(i, ":", self.user_details[i])
        except Exception as e:
            print("\n!! Something went wrong please try again !!\n ")
            
    def user_login(self):
        try:
            while True:
                print(f"Welcome TO {self.restro_name} Restaurant\n\nPlease Sign In")
                email=input("Enter Your Email ID : ")
                pas=input("Enter Your Password : ")
                if len(self.user_details)!=0:
                    if email==self.user_details["Email_ID"]:
                        if pas==self.user_details["Password"]:
                            print("\n!! Login successfully !!")
                            break
                        else:
                            print("\n!! Invalid Password !!\n")
                    else:
                        print("\n!! Invalid Email ID !!\n")
                else:
                    print("\n! There is no Account with this Email ID !\n\n!! Please Creat Your Account First!!\n")
                    self.user_register()
                    print("!! Your account is created Successfully !!\n")

        except Exception as e:
            print("\n!! Something went wrong please try again !!")
                
    def place_order(self):
        try:
            menu=["1. Tandoori Chicken (4 pieces) [INR 240]", "2. Vegan Burger (1 Piece) [INR 320]","3.Truffle Cake (500gm) [INR 900]"]
            print("Menu Food List")
            for i in menu:
                print(i)
            while True:
                print("\nEnter 1 to Place the Order\nEnter 2 to Exit ")
                x=input()
                if x=="1":
                    print("Enter the Food number You want to ordered separated by comma")
                    y=input().split(",")
                    for i in y:
                        z=int(i)
                        if z<=len(menu):
                            self.ordered_item.append(menu[z-1])
                        else:
                            print("Sorry We Don't this Food Item : ",z)
                    print("\nList of food item you selected : \n")
                    for j in self.ordered_item:
                        print(j)
                elif x=="2":
                    break
                else:
                    print("!! Invalid Number !!\n")
        except Exception as e:
            print("\n!! Something went wrong try again !!")       
                
    def ordered_history(self):
        print("\nList of Previous ordered : ")
        for i in self.ordered_item:
            print(i)
            
    def update_details(self):
        try:
            while True:
                print("Select Below Options to Update Your Profile Details\n")
                print("1. Name\n2. Phone number\n3. Email ID\n4. Password\n5. Address\n6. Exit\n")
                x=input()
                if x=="1":
                    self.user_details["User Name"]=input("Enter your updated full name : ")
                    print("\n!! Detail Updated Successfully !!\n")
                elif x=="2":
                    self.user_details["Phone No."]=int(input("Enter your updated 10 digit phone number : "))
                    print("\n!! Detail Updated Successfully !!\n")      
                elif x=="3":
                    self.user_details["Email_ID"]=input("Enter your updated email id : ")
                    print("\n!! Detail Updated Successfully !!")
                    
                elif x=="4":
                    self.user_details["Password"]=input("Enter your updated password : ")
                    print("\n!! Detail Updated Successfully !!\n")
                    
                elif x=="5":
                    self.user_details["Address"]=input("Enter your updated address with area PIN code ")
                    print("\n!! Detail Updated Successfully !!\n")
                    
                elif x=="6":
                    break
                else:
                    print("\n!! Invalid Number Entered !!\n")
                    
                if x in ["1","2","3",'4',"5","6"]:
                    for i in self.user_details:
                        print(i, ":",self.user_details[i])
                else:
                    print("\nUser Updated Details :\n")      
        except Exception as e:
            print("\n!! Something went wrong please try again !!\n ")
            
            
       # defining the Main function to run the code in one shot     

try:
    def main():
        obj=Restaurant("ITC  INTERNATIONAL")
        print(f"!!  Welcome To {obj.restro_name} Restaurant  !!\n")
        print("!!----------------------------------------------------------")
        print("\nHellow Guys\n What you want to eat in my Restro ? Its a treat from my side :)")
        print("-----------------------------------------------------------!!\n")
        
        while True:
            print("1. Admin\n2. User\n3. Exit\n")
            x=input()
            if x=="1":
                while True:
                    print("1. Add New Food Items\n2. Edit Food Items\n3. View Food Items \n4. Delete Food Items\n5. Exit")
                    y=input()
                    if y=="1":
                        obj.add_food_item()
                    elif y=="2":
                        obj.edit_food_item()
                    elif y=="3":
                        obj.view_food_item()
                    elif y=="4":
                        obj.delete_food_item()
                    elif y=="5":
                        break
                    else:
                        print("Invalid Number")
            elif x=="2":
                while True:
                    print("\nEnter the Below Options\n")
                    print("1. Register\n2. Login\n3. Exit\n")
                    y=input()
                    if y=="1":
                        obj.user_register()
                    elif y=="2":
                        obj.user_login()
                        while True:
                            print("\nEnter the Below Options\n")
                            print("1. Place New Order\n2. Check Order History\n3. Update Your Profile Details\n4. Exit")
                            z=input()
                            if z=="1":
                                obj.place_order()
                            elif z=="2":
                                obj.ordered_history()
                            elif z=="3":
                                obj.update_details()
                            elif z=="4":
                                break
                            else:
                                print("invalid Number")            
                    elif y=="3":
                        break
                    else:
                        print("\nInvalid Number ")        
            elif x=="3":
                break
            else:
                print("Invalid Number")
except Exception as e:
    print("something went wrong please give input carefully")
            
        # calling the main function 
        
if __name__=='__main__':
    main()

print("THANK YOU SIR")
