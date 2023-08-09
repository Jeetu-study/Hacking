# Encryption  

***ye symmetric or asymmetric ka concept hain jiske under symmetric Encryption ke under single key ka use kiya jata hai kisi bhi text ko encrypt or decrypt krne ke liye --- or asymmetric Encryption ke under public key or private key ka consept ata hai jiske under public key se encrypt or usi publie key ki private key se us text ko decrypt kiya jaa sakta hai***


# Hashing

***hashing ke under SH256 , MD5 ,SHA-1, Bcrypt or bhi bhut sare hashing ate hai jo kisi bhi text ko ya file ka ek hash create kr dete hai even agar us file ke under ek byte ka bhi change ho to hash value total change ho jati hai https ssl certificate***


# Encoding

***Encoding reversible hota hai, matlab original data ko wapis recover kiya ja sakta hai.  like Url encoding , Base64 encoding , Html encoding***


# SQL INJECTION

***Step 1  kisi bhi application ke coloums ko find krna <br/>
<b> https://example.com/?id=1' ORDER BY 1-- </b> <br/>
order by ko increse krte jao jis point per error aya ya application diffrent response kre utne coloum hai example 6 coloum hai***<br/>

***Step 2 <br/>
https://example.com/?id=1' UNION SELECT ALL 1,2,3,4,5,6--<br/>
perticular table ke coloums ke bare main pata krna ki konse coloum se hum apni query ko db main insert krwa rahe hai***

***Step 3 <br/>
https://example.com/?id=1' UNION SELECT ALL 1,@@version,3,4,5,6--<br/>
vulnerble coloum milne ke baad waha se hum db ki informations version jaise data ko retrive kr sakte hai***

**NOTES SQL DB ke under information_schema krke ek table create hota hai jiske under sari informations hoti hai like table coloum names kya hai or kisi perticular coloum ka datatype kya hai**

***Step 4 retrive all tables name with the help of information_schema.tables function <br/>
https://example.com/?id=1' UNION SELECT ALL 1,group_concat(table_name),3,4,5 from information_schema.tables where table_schema=database()--
<br/>
Yha per humne group_concat kiya hai jiska matlb hota hai ki Is function ke through aap multiple rows ke values ko ek hi column mein combine kar sakte hain aur unhe comma ya koi specific delimiter ke sath separate kar sakte hain. Isse aapko data ko organized aur readable format mein dekhne mein madad milti hai. to data kuch ese show karega jeetu,jassi,mayur jabki ye data alg alg coloum main tha but ek coloum ke under aa gaya ab information_schema.tables use kiya jsike under sare tables and coloum ki details unka datatype sabki information hoti hai to hum vo sari info information_schema se nikal rahe hai or last main jo database hoga vo vo kuch bhi ho to humne database() ye kr diya***


***Step 5 retrive all coloums name with the help of information_schema.coloums function <br/>
https://example.com/?id=1' UNION SELECT ALL 1,group_concat(colums_name),3,4,5 from information_schema.coloums where table_schema=database() and table_name = 'table-name-here'--
<br/>
yaha per jo information_schema function se jo tables name mili thi us table ka naam table-name-here per dalna hai taki hum particular tables ke coloums ki information retrive kr sake***


***Step 6 <br/>
https://example.com/?id=1' UNION SELECT ALL 1,group_concat(password,0x20,username),3,4,5 FROM table-name-here--
<br/>
upper humko information_schema se coloum name and tables mil gayi ab jo coloum ke under senstive info ho usko hum retrive krenge like username, password . humne yaha per bhi group_concat use kiya hai taki sara result ek coloum main show ho or 0x20 ka use isliye kiya taki data jab show ho to clear dikhe ye ek space ka kaam krega***



