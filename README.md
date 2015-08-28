credit to

https://twitter.com/R00tkitSMM 

https://twitter.com/mtp1376

never login to telegram if you see tdata , maybe you try to make valid token for someone else :)
___

#The Bug
based on our researches on (https://github.com/telegramdesktop/tdesktop), we found a Session Fixation bug, which could lead to full account hijack, alongside with bypassing two-step verification and logging in without any sessions getting recorded.

#what is  session Fixation 
In computer network security, session fixation attacks attempt to exploit the vulnerability of a system which allows one person to fixate (set) another person's session identifier (SID). Most session fixation attacks are web based, and most rely on session identifiers being accepted from URLs (query string) or POST data.

#Preface
Telegram Desktop application does not generate a new token for login when an invalid token(not logged in) is there in the tdata folder.
So that if we put an invalid token inside a tdata folder in someone's Telegram folder, our invalid token get's used for login, and  our invalid token is valid and we'll be able to hijack his account, without creating any sessions on his account, and off course bypassing two-step verification.

#Description
The Session Fixation bug appears on the app because when a session is try to Create  in registration time , the ivalid token( token for  already closed session ) is used , insted  of createing new toke

So that if you do the following steps, you can demo the bug:

1. Get a copy of Telegram Desktop application.
2. Login using one of your accounts to Telegram.
3. Copy the tdata folder (or the whole Telegram folder (just tdata matters)) to somewhere else.
4. Kill the session you opened in step 2 on your other device; so that both Telegram folders now are logged out.
5. Use one of those Telegram folder copies to login to another Telegram account.
6. Now if you open the other folder, it will open the same session as the other one.

It IS a bug for sure, and it's (https://www.owasp.org/index.php/Session_fixation).

so again never login to telegram if you see tdata , maybe  you try to make valid token for  someone else  :)
