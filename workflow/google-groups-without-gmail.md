---
headline: 'Signup to Google Groups without Gmail'
date: 2016-08-14
category: workflow
tags:
  - email
  - google-groups
---

Wanted to sign up to a google groups mailing list with a non google email account. [Google Groups Help] is not very helpful with this.

Tried to email `[Group-Name]+subscribe@googlegroups.com` but that didnt want to work for me. Using the URL method did:

```
http://groups.google.com/group/GROUP-NAME/boxsubscribe?email=[EMAIL]
```

- Be sure to log out of all google accounts and clear browser
- If receiving email to a gmail account, copy the confirmation link, logout of gmail and clear browser. Then `paste and go`.

---
- [source](http://webapps.stackexchange.com/a/13510)

[Google Groups Help]: https://support.google.com/groups#topic=9216