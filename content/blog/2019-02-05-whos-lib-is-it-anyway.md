+++
title = "Who’s Lib is it Anyway?"
date = 2019-02-05
taxonomies = { tags = ["Android", "programming"] }
+++

Working with Android SDKs can be a bit like inviting someone to store their vintage land-mine collection in your back yard (and then paying them for that convenience).

I recently needed to answer, “Who’s the asshole bringing in these symbols?” and this is how I found out.

For JAR files...
> Search JAR files for ‘android.arch.lifecycle’ symbols.
> ```shell
> find . -name "*.jar" -type f -print \
>   -exec sh -c "jar -tf {} | grep android\/arch\/lifecycle" \;
> ```

...and then for AAR files...

> Search AAR files for ‘android.arch.lifecycle’ symbols.
> ```shell
> find . -name "*.aar" -type f -print \
>   -exec sh -c "unzip -p -j {} classes.jar | jar -t | grep android\/arch\/lifecycle" \;
> ```

These commands are looking for ‘android.arch.lifecycle’ symbols, so replace that with whatever it is you are looking for.

## headdesk

This functionality is also available in the headdesk blame command, starting in version 0.11.0.

### headdesk blame android.arch.lifecycle
![headdesk blame android.arch.lifecycle](/images/headdesk-blame.png)
