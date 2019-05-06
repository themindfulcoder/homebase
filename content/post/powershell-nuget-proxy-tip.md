---
title: "Powershell Nuget Proxy Tip"
date: 2019-05-06
draft: false
---

Let's toggle nuget proxy configuration with a powershell alias.

Using public nuget sources as well as private sources through a proxy can be tulmiltuous at times. That's why I wrote a little script to toggle the nuget proxy and enable or disable the private source depending on my location and sort of project I'm working on.

First the script
```
$proxy = 'my-corp-proxy.com:8080'
$source = "Private-Repository"

$value = (nuget config HTTP_PROXY 2> $null)
if ($proxy -eq $value)
{
    nuget config -Set HTTP_PROXY=
    Write-Host The $value proxy was removed.
    nuget sources Disable -Name "$source"
}
else {
    nuget config -Set HTTP_PROXY="$proxy"
    Write-Host The $proxy proxy was applied.
    nuget source Enable -Name "$source"
}
```

First we defined a `proxy` and it's associated `source`. We compare the defined proxy with the current 
configuration and when it's the same, we remove the proxy configuration and source; when it's 
different, we apply the defined proxy and source

Now that we have a script we can quickly run it to toggle between two proxy/source profiles.

I stored it with a pretty long name, nested in some folders and getting to the script was still pretty 
laborious. So I also used a powershell alias to make it more memorable and conventient to use.

`Set-Alias -Name nuget-proxy-toggle -Value C:\Path\To\My\Nested\Very-long-name-powershell-script.ps1`

This only sets it for the session, to have it available in any of your powershell instances, you can 
modify your powershell profile.

`notepad $profile` will open your powershell profile. Add the `Set-Alias` command from earlier to 
this file and save it.


