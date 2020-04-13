---
layout: doc
description: App protection policies protect application data from attacks based on keyloggers and/or screen capture tools. Allow companies to embrace BYOD, and extend resources to remote workers, contractors, and gig economy workers.
---
# App protection policies

## Contributors

**Author:** [Mayank Singh](https://twitter.com/techmayank)

**Special Thanks:** [Martin Zugec](https://twitter.com/MartinZugec) and [Arvind Sankarasubramanian](https://twitter.com/arvind_sa20)

The end user is widely considered the weakest piece on the attack surface of an organization. It has become common practice for attackers to use sophisticated methods to fool users into installing malware on their endpoints. Once installed, the malware can silently collect and exfiltrate sensitive data such as user’s credentials, sensitive information, company’s intellectual property, or confidential data. With increase in BYO devices and access of corporate resources from unmanaged endpoints, endpoints become an even more exposed threat surface. With many users working from home, the risk to the organizations is heightened due to the untrustworthiness of the endpoint device.

When accessing a virtual app or virtual desktop session, the attack surface is drastically reduced. The virtual session is not running on the endpoint and users generally do not have permission to install apps within the virtual session. The data within the session is secure in the data center or cloud resource location. However, a compromised endpoint can capture session keystrokes and information displayed on the endpoint. Citrix provides administrators the ability prevent these attack vectors, using an add-on feature called App protection. The feature enables Citrix Virtual Apps and Desktops (CVAD) administrators to enforce policies specifically on one or more delivery groups. When users connect to sessions from these delivery groups, the user’s endpoint has either anti screen capture or anti-keylogging or both enforced on the endpoints.

## Features

App protection policies protect client endpoints running Windows Desktop OSes (Windows 10, Windows 8.1, and Windows 7). All versions of macOS that the Citrix Workspace app for Mac supports are also protected.

App protection policies work by controlling access to specific API calls of the underlying OS, required to capture screens or keyboard presses. App protection policies can therefore provide protection even against custom and purpose-built hacker tools. However, as OSes evolve, new ways of capturing screens and logging keys can emerge. While Citrix continues to identify and address, Citrix cannot guarantee full protection in specific configurations and deployments.

When a user logs into StoreFront, security capabilities of the endpoint are assessed and matched against available resources. Applications and desktops protected by App protection policies are visible only if an endpoint meets the security requirements. One such requirement is a check if the App protection components are installed.

[![App_protection_policies_Protect_CWA_dialogs](/en-us/tech-zone/learn/media/tech-briefs_app-protection-policies_3-anti-keylogging-auth-dialog-ss.png)](/en-us/tech-zone/learn/media/tech-briefs_app-protection-policies_3-anti-keylogging-auth-dialog-ss.png)

Since these features are based on the Citrix Workspace app, they protect not only the in session screens for Windows or MAC desktops/apps but also the Citrix Workspace app dialogs, which include authentication screens.

## Anti-keylogging

A keylogger is one of the attacker’s favored tools of data exfiltration, as it can remain on an infected machine without doing any noticeable damage. All the keystrokes entered by the user are harvested, including user name / password combinations, credit cards numbers, and confidential data. The harvested data is then silently exfiltrated later on.

With encryption, the app protection’s anti-keylogging garbles the text the user is typing for both physical and on-screen keyboards. The anti-keylogging feature encrypts the text before any keylogging tool can access it from the kernel/OS level. A keylogger installed on the client endpoint, reading the data from the OS/driver, would capture gibberish instead of the keystrokes the user is typing.

[![App_protection_policies_Anti_Keylogging](/en-us/tech-zone/learn/media/tech-briefs_app-protection-policies_1-anti-keylogging-ss.png)](/en-us/tech-zone/learn/media/tech-briefs_app-protection-policies_1-anti-keylogging-ss.png)

## Anti screen capture

Anti screen capture prevents an app from attempting to take a screenshot of or a recording of the screen within a virtual app or desktop session. The screen capture software would be unable to detect content within the capture region. The area selected by the app is grayed out or the app captures nothing instead of the screen section that it expects to copy. The anti screen capture feature applies to snip and sketch, snipping tool, Shift+Ctrl+Print Screen on Windows. Screen recording tools and meeting / web conferencing applications such as GoToMeeting and Teams, on both Windows and macOS are also included.

[![App_protection_policies_Anti_screen_capture](/en-us/tech-zone/learn/media/tech-briefs_app-protection-policies_2-anti-screen-capture-ss.png)](/en-us/tech-zone/learn/media/tech-briefs_app-protection-policies_2-anti-screen-capture-ss.png)

The anti screen capture protection is active only when any of the protected apps are on screen. If any part of the window displaying the app is on screen then the policies disable screen captures.
If the user wants to take a screenshot of the client endpoint’s screen / other apps, while a protected app is running on the endpoint, then the user must minimize the protected app.

The protection extends to files from [Citrix Files](/en-us/mobile-productivity-apps/citrix-files.html) or any other connectors like Google Drive or Microsoft OneDrive that are accessed from within Citrix Workspace app. The apps are protected from screen scrapers, as are all the microapps and their notifications from within Workspace.

## Considerations

*  App protection policies are configured on the Desktop Delivery Controller. Administrators identify the delivery groups to be protected by applying the policy on them. Read more about configuration and compatibility in our [technical docs](/en-us/citrix-virtual-apps-desktops/secure/app-protection.html)

*  App protection policies require a minimum of Citrix Virtual Apps and Desktops version 1912 installed on Desktop Delivery Controller and StoreFront. App protection policies are implemented on the client end point and control data sent from the Citrix Workspace app to the client’s OS. Therefore, there is no dependency on the state or version of the VDA installed in the session.

*  The required versions of the Citrix Workspace app are:
    *  Citrix Workspace app 1912 for Windows (LTSR) and later
    *  Citrix Workspace app 2001 for Mac and later

    The HTML5 client is not supported.

*  If users connect from an older version than Citrix Workspace app 1912 for Windows or Citrix Workspace app 2001 for Mac, or from Citrix Receiver, then the tagged resources (to be protected) are not enumerated in the StoreFront.

*  App protection policies don’t co-exist the Client Clipboard Redirection policies. The Client Clipboard Redirection policies must be disabled to ensure that App protection works.

*  App protection policies are unsupported in a double hop (nested) scenario or if a user is using Remote Desktop Protocol to access the Citrix session. For nested sessions, the first hop must be to a Windows desktop operating system and then the user must launch a second Citrix session from within it for the protections to apply.

## Summary

App protection policies can help protect application data from attackers that have surreptitiously installed either a keylogger or screen capture tools or both on endpoints. App protection policies allow companies to embrace [BYOD](https://www.citrix.com/glossary/byod.html), and extend resources to [remote workers](/en-us/tech-zone/learn/tech-briefs/business-continuity.html), contractors, and gig economy workers.