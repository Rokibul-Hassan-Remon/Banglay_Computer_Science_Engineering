### **Root User's Home Directory (`/root`)**

- যখন আপনি root user হিসেবে লগইন করেন, তখন আপনার home directory সাধারণত /root হয়।  
- `cd` কমান্ড কোনো arguments ছাড়া চালালে সাধারণত এটি আপনাকে /root-এ নিয়ে যায়। 
```shell
		cd 
```
- যদি /root অনুপস্থিত থাকে, সঠিকভাবে সেটআপ না করা থাকে, অথবা আপনার HOME environment variable `/` নির্দেশ করে, তাহলে `cd` কমান্ড আপনাকে root directory (`/`) তে নিয়ে যেতে পারে।

---

### **Root Directory (`/`)**

- Root directory (`/`) হল Linux filesystem-এর top-level directory। এটি এমন essential system directories ধারণ করে যেমন bin, etc, home, এবং আরও অনেক কিছু।  
- `cd /` চালালে সর্বদা current directory `/` এ পরিবর্তিত হয়।
```shell
		cd  /
```


