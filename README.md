# my
import mysql.connector as reg

while True:
    print("1:show senior groups of NCSC")
    print("2:show junior groups of NCSC")
    ch=int(input("enter the choice:"))
    if ch==1:
        print("show senior group of NCSC")
        while True:
            print("1:registartion")
            print("2:evaluation")
            print("3:result")
            print("4:EXIT")
            con=reg.connect(host="localhost",user="root",passwd="Renuka@120306",database="NCSC")
            print("connected sucessfully")
            cur=con.cursor()
            print("cursor created")
            ch=int(input("enter the choice:"))
            if ch==1:
                print("Registertion")
                while True:
                    print("1:to insert")
                    print("2:to update")
                    print("3:to delete")
                    print("4:to dispaly")
                    print("5:EXIT")
                    ch=int(input("enter the choice:"))
                    if ch==1:
                        print("to insert")
                        SID=input("enter the SID:")
                        name=input("enter the Name:")
                        clas=int(input("enter the class:"))
                        sec=input("enter the section:")
                        dob=input("enter the dob(YYYY-MM-DD):")
                        name_of_the_school=input("enter the school name:")
                        gender=input("enter the gender(M/F):")
                        themeid=int(input("enter the themeid:"))
                        topic=input("enter the topic:")
                        sql="insert into registration values('{}','{}',{},'{}','{}','{}','{}',{},'{}')".format(SID,name,clas,sec,dob,name_of_the_school,gender,themeid,topic)

                        cur.execute(sql)
                        con.commit()
                        con.close()
                        break
                    elif ch==2:
                            print("to update:")
                            while True:
                                print("1:to update dob")
                                print("2:to update class")
                                print("3:EXIT")
                                ch=int(input("enter the choice:"))
                                if ch==1:
                                    print("to update dob")
                                    SID=input("enter the SID :")
                                    dob=input("enter the new dob(YYYY-MM-DD):")
                                    sql="update registration set dob='{}' where SID='{}'".format(dob,SID)
                                    cur.execute(sql)
                                    con.commit()
                                    con.close
                                    break
                                elif ch==2:
                                    print("to update class")
                                    SID=input("enter the SID :")
                                    clas=input("enter the correct class:")
                                    sql="update registration set class={} where SID='{}'".format(clas,SID)
                                    cur.execute(sql)
                                    con.commit()
                                    con.close
                                    break
                                elif ch==3:
                                    print("EXIT")
                                    break
                    if ch==3:
                        print("to delete")
                        print("1: student is eliminated")
                        print("2: student record doesnot exists")
                        ch=int(input("enter the choice:"))
                        SID=input("enter the SID :")
                        sql="delete from registration where SID='{}'".format(SID)
                        cur.execute(sql)
                        con.commit()
                        con.close
                        break
                    if ch==4:
                        print("to display")
                        sql2="select *  from registration"
                        cur.execute(sql2)
                        RECS=cur.fetchall()
                        for rec in RECS:
                            SID=rec[0]
                            name=rec[1]
                            clas=rec[2]
                            sec=rec[3]
                            dob=rec[4]
                            name_of_the_school=rec[5]
                            gender=rec[6]
                            themeid=rec[7]
                            topic=rec[8]
                            lst=[SID,name,clas,sec,dob,name_of_the_school,gender,themeid,topic]
                            print(lst)
                        break
                    if ch==5:
                        print("EXIT")
                        break
            elif ch==2:
                print("EVALUATION")
                while True:
                    print("1:to insert")
                    print("2:to update")
                    print("3:to display")
                    print("4:EXIT")
                    ch=int(input("enter the choice:"))
                    if ch==1:
                        print("to insert")
                        Judgeid=input("enter the jid:")
                        SID=input("enter the SID:")
                        E1=int(input("enter the marks out of 50:"))
                        E2=int(input("enter the marks out of 50:"))
                        E3=int(input("enter the marks out of 50:"))
                        total=E1+E2+E3
                        sql="insert into EVALUATION values('{}','{}',{},{},{},{})".format(Judgeid,SID,E1,E2,E3,total)
                        cur.execute(sql)
                        con.commit()
                        con.close()
                        break
                      
                    if ch==2:
                        print("to update")
                        while True:
                            print("1:to update E1:")
                            print("2:to update E2:")
                            print("3:to update E3:")
                            print("4:to update SID:")
                            print("5:EXIT")
                            ch=int(input("enter the choice:"))
                            if ch==1:
                                print("cursor created")
                                SID=input("enter the SID :")
                                Judgeid=input("enter the Judgeid:")
                                E1=int(input("enter the correct E1:"))
                                sql="update evaluation set E1={} where SID={} and Judgeid={}".format(E1,SID,Judgeid)
                                cur.execute(sql)
                                con.commit()
                                con.close
                                break
                            elif ch==2:
                                print("to update E2")
                                SID=input("enter the SID :")
                                Judgeid=input("enter the Judgeid:")
                                E2=int(input("enter the correct E2:"))
                                sql="update evaluation set E2={} where SID={} and Judgeid={}".format(E2,SID,Judgeid)
                                cur.execute(sql)
                                con.commit()
                                con.close
                                break
                            elif ch==3:
                                print("to update E3")
                                SID=input("enter the SID :")
                                Judgeid=input("enter the Judgeid:")
                                E3=int(input("enter the correct E3:"))
                                sql="update evaluation set E3={} where SID={} and Judgeid={}".format(E3,SID,Judgeid)
                                cur.execute(sql)
                                con.commit()
                                con.close
                                break
                            elif ch==4:
                                print("to update SID")
                                total=input("enter the total:")
                                SID=input("enten the correct SID:")
                                Judgeid=input("enter the Judgeid:")
                                sql="update evaluation set SID={} where Judgeid={}".format(SID,Judgeid)
                                cur.execute(sql)
                                con.commit()
                                con.close()
                                break
                            elif ch==5:
                                print("EXIT")
                                break
                            
                    if ch==3:
                        print("to display")
                        sql2="select *  from EVALUATION"
                        cur.execute(sql2)
                        RECS=cur.fetchall()
                        for rec in RECS:
                            jugdeid=rec[0]
                            SID=rec[1]
                            E1=rec[2]
                            E2=rec[3]
                            E3=rec[4]
                            total=rec[5]
                            lst=[jugdeid,SID,E1,E2,E3,total]
                            print(lst)
                        break
                    if ch==4:
                         print("EXIT")
                         break

            elif ch==3:
                print("Resuts")
                sql="select SID,sum(total) from evaluation group by SID order by sum(total) desc ;"
                cur.execute(sql)
                lst=[]
                recs=cur.fetchall()
                for rec in recs:
                    lst.append(rec[0])
                print(lst)
                
                first=lst[0]
                second=lst[1]
                thrid=lst[2]
                total=[first,second,thrid]
                print(total[0],": 1st")
                print(total[1],": 2nd")
                print(total[2],": 3rd")
                SID=total[0]
                sql1="select name from registration where SID='{}'".format(SID)
                cur.execute(sql1)
                rec1=cur.fetchall()
                print(rec1,":1st price")
                SID=total[1]
                sql1="select name from registration where SID='{}'".format(SID)
                cur.execute(sql1)
                rec2=cur.fetchall()
                print(rec2,":2nd price")
                SID=total[2]
                sql1="select name from registration where SID='{}'".format(SID)
                cur.execute(sql1)
                rec3=cur.fetchall()
                print(rec3,":3rd price")
                    
                con.commit()
                con.close()
                break
                
                
            else:
                print("thank you")
            break
    elif ch==2:
        print("show junior groups of NCSC")
        while True:
            print("1:registartion")
            print("2:evaluation")
            print("3:result")
            print("4:EXIT")
            con=reg.connect(host="localhost",user="root",passwd="Renuka@120306",database="NCSC")
            print("connected sucessfully")
            cur=con.cursor()
            print("cursor created")
            ch=int(input("enter the choice:"))
            if ch==1:
                print("Registertion")
                while True:
                    print("1:to insert")
                    print("2:to update")
                    print("3:to delete")
                    print("4:to dispaly")
                    print("5:EXIT")
                    ch=int(input("enter the choice:"))
                    if ch==1:
                        print("to insert")
                        SID=input("enter the SID:")
                        name=input("enter the Name:")
                        clas=int(input("enter the class:"))
                        sec=input("enter the section:")
                        dob=input("enter the dob(YYYY-MM-DD):")
                        name_of_the_school=input("enter the school name:")
                        gender=input("enter the gender(M/F):")
                        themeid=int(input("enter the themeid:"))
                        
                        sql="insert into registration_Ju values('{}','{}',{},'{}','{}','{}','{}',{})".format(SID,name,clas,sec,dob,name_of_the_school,gender,themeid)

                        cur.execute(sql)
                        con.commit()
                        con.close()
                        break
                    elif ch==2:
                            print("to update:")
                            while True:
                                print("1:to update dob")
                                print("2:to update class")
                                print("3:EXIT")
                                ch=int(input("enter the choice:"))
                                if ch==1:
                                    print("to update dob")
                                    SID=input("enter the SID :")
                                    dob=input("enter the new dob(YYYY-MM-DD):")
                                    sql="update registration_Ju set dob={} where SID={}".format(dob,SID)
                                    cur.execute(sql)
                                    con.commit()
                                    con.close
                                    break
                                elif ch==2:
                                    print("to update class")
                                    SID=input("enter the SID :")
                                    clas=input("enter the correct class:")
                                    sql="update registration_Ju set class={} where SID={}".format(clas,SID)
                                    cur.execute(sql)
                                    con.commit()
                                    con.close
                                    break
                                elif ch==3:
                                    print("EXIT")
                                    break
                    if ch==3:
                        print("to delete")
                        print("1: student is eliminated")
                        print("2: student record doesnot exists")
                        ch=int(input("enter the choice:"))
                        SID=input("enter the SID :")
                        sql="delete from registration_Ju where SID={}".format(SID)
                        cur.execute(sql)
                        con.commit()
                        con.close
                        break
                    if ch==4:
                        print("to display")
                        sql2="select *  from registration_Ju"
                        cur.execute(sql2)
                        RECS=cur.fetchall()
                        for rec in RECS:
                            SID=rec[0]
                            name=rec[1]
                            clas=rec[2]
                            sec=rec[3]
                            dob=rec[4]
                            name_of_the_school=rec[5]
                            gender=rec[6]
                            themeid=rec[7]
                            
                            lst=[SID,name,clas,sec,dob,name_of_the_school,gender,themeid]
                            print(lst)
                        break
                    if ch==5:
                        print("EXIT")
                        break
            elif ch==2:
                print("EVALUATION")
                while True:
                    print("1:to insert")
                    print("2:to update")
                    print("3:to display")
                    print("4:EXIT")
                    ch=int(input("enter the choice:"))
                    if ch==1:
                        print("to insert")
                        Judgeid=input("enter the jid:")
                        SID=input("enter the SID:")
                        E1=int(input("enter the marks out of 50:"))
                        E2=int(input("enter the marks out of 50:"))
                        E3=int(input("enter the marks out of 50:"))
                        total=E1+E2+E3
                        sql="insert into EVALUATION_Ju values('{}','{}',{},{},{},{})".format(Judgeid,SID,E1,E2,E3,total)
                        cur.execute(sql)
                        con.commit()
                        con.close()
                        break
                      
                    if ch==2:
                        print("to update")
                        while True:
                            print("1:to update E1:")
                            print("2:to update E2:")
                            print("3:to update E3:")
                            print("4:to update SID:")
                            print("5:EXIT")
                            ch=int(input("enter the choice:"))
                            if ch==1:
                            
                                SID=input("enter the SID :")
                                Judgeid=input("enter the Judgeid:")
                                E1=int(input("enter the correct E1:"))
                                sql="update evaluation_Ju set E1={} where SID='{}' and Judgeid='{}'".format(E1,SID,Judgeid)
                                cur.execute(sql)
                                con.commit()
                                con.close
                                break
                            elif ch==2:
                                print("to update E2")
                                SID=input("enter the SID :")
                                Judgeid=input("enter the Judgeid:")
                                E2=int(input("enter the correct E2:"))
                                sql="update evaluation_Ju set E2={} where SID='{}' and Judgeid='{}'".format(E2,SID,Judgeid)
                                cur.execute(sql)
                                con.commit()
                                con.close
                                break
                            elif ch==3:
                                print("to update E3")
                                SID=input("enter the SID :")
                                Judgeid=input("enter the Judgeid:")
                                E3=int(input("enter the correct E3:"))
                                sql="update evaluation_Ju set E3={} where SID='{}' and Judgeid='{}'".format(E3,SID,Judgeid)
                                cur.execute(sql)
                                con.commit()
                                con.close
                                break
                            elif ch==4:
                                print("to update SID")
                                total=input("enter the total:")
                                SID=input("enten the correct SID:")
                                Judgeid=input("enter the Judgeid:")
                                sql="update evaluation_Ju set SID='{}' where Judgeid='{}'".format(SID,Judgeid)
                                cur.execute(sql)
                                con.commit()
                                con.close()
                                break
                            elif ch==5:
                                print("EXIT")
                            break
                            
                    if ch==3:
                        print("to display")
                        sql2="select *  from EVALUATION_Ju"
                        cur.execute(sql2)
                        RECS=cur.fetchall()
                        for rec in RECS:
                            jugdeid=rec[0]
                            SID=rec[1]
                            E1=rec[2]
                            E2=rec[3]
                            E3=rec[4]
                            total=rec[5]
                            lst=[jugdeid,SID,E1,E2,E3,total]
                            print(lst)
                        break
                    if ch==4:
                         print("EXIT")
                         break

            elif ch==3:
                print("Resuts")
                sql="select SID,sum(total) from evaluation_Ju group by SID order by sum(total) desc ;"
                cur.execute(sql)
                lst=[]
                recs=cur.fetchall()
                for rec in recs:
                    lst.append(rec[0])
                print(lst)
                
                first=lst[0]
                second=lst[1]
                thrid=lst[2]
                total=[first,second,thrid]
                print(total[0],": 1st")
                print(total[1],": 2nd")
                print(total[2],": 3rd")
                SID=total[0]
                sql1="select name from registration_Ju where SID='{}'".format(SID)
                cur.execute(sql1)
                rec1=cur.fetchall()
                print(rec1,":1st price")
                SID=total[1]
                sql1="select name from registration_Ju where SID='{}'".format(SID)
                cur.execute(sql1)
                rec2=cur.fetchall()
                print(rec2,":2nd price")
                SID=total[2]
                sql1="select name from registration_Ju where SID='{}'".format(SID)
                cur.execute(sql1)
                rec3=cur.fetchall()
                print(rec3,":3rd price")
                    
                con.commit()
                con.close()
                break
                
                
            else:
                print("thank you")
            break
