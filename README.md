# Health-Diet-and-Excersize-chart
emp_name={1:"Zulfkar",2:"Khan",3:"Ali"}
log={1:"Diet",2:"Excersize"}
# print(type(emp_name))
def getdate():
    import datetime
    return datetime.datetime.now()
print(getdate())
try:
    process="y"
    while(process=="y"):
        print("Select Employee Name :")
        for key,data in emp_name.items():
            print("Press ",key," for ",data," : \n",end="")
        name=int(input())
        print("Select client is ",emp_name[name],"\n Select \n1 for Log \n2 for Retrieve :")
        op=int(input())
        if op is 1:
            for key,data in log.items():
                print("Press ",key," for ",data," : \n",end="")
            action=int(input())
            print("Selected action is ",log[action])
            fp=open(emp_name[name]+"_"+log[action]+".txt","a")
            pp="y"
            while(pp=="y"):
                print("Enter ",log[action],"\n",end="")
                text=input()
                text=text.capitalize()
                # print(text)
                fp.write("["+str(getdate())+"]\t"+text+"\n")
                # fp.write("["+getdate()+"]\t"+text+"\n")
                pp=input("Do you Want to Continue y/n :")
            fp.close()
        elif op is 2:
            for key,data in log.items():
                print("Press ",key," for ",data," : \n",end="")
            action=int(input())
            print(emp_name[name],"_",log[action]," Report : \n",end="")
            fp=open(emp_name[name]+"_"+log[action]+".txt")
            content=fp.readlines()
            for line in content:
                print(line,end=" ")
            fp.close()
        else:
            print("Wrong Input !!")    
        process=input("Do u want to Continue this Process ,Press y for Yes, n for No :")
except Exception as e:
    print("Error is :",e)
