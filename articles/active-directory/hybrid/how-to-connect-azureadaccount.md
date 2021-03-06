---
title: 'Azure AD Connect sync: How to manage the Azure AD service account | Microsoft Docs'
description: This topic documents how to restore the Azure AD service account.
services: active-directory
keywords: AADSTS70002, AADSTS50054, How to reset the password for the Azure AD Connect sync Connector service account
documentationcenter: ''
author: billmath
manager: daveba
editor: ''

ms.assetid: 6077043a-27f1-4304-a44b-81dc46620f24
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: conceptual
ms.date: 07/12/2017
ms.subservice: hybrid
ms.author: billmath

---
# Azure AD Connect sync: How to manage the Azure AD service account
The service account used by the Azure AD Connector is supposed to be service free. If you need to reset its credentials, then this topic is for you. For example, if a Global Administrator has by mistake reset the password on the service account using PowerShell.

## Reset the credentials
If the service account defined on the Azure AD Connector cannot contact Azure AD due to authentication problems, the password can be reset.

1. Sign in to the Azure AD Connect sync server and start PowerShell.
2. Run `Add-ADSyncAADServiceAccount`.  
   ![PowerShell cmdlet addadsyncaadserviceaccount](./media/how-to-connect-azureadaccount/addadsyncaadserviceaccount.png)
3. Provide Azure AD Global admin credentials.

This cmdlet resets the password for the service account and update it both in Azure AD and in the sync engine.

## Known issues these steps can solve
This section is a list of errors reported by customers that were fixed by a credentials reset on the Azure AD service account.

- - -
Event 6900  
The server encountered an unexpected error while processing a password change notification:  
AADSTS70002: Error validating credentials. AADSTS50054: Old password is used for authentication.

- - -
Event 659  
Error while retrieving password policy sync configuration. Microsoft.IdentityModel.Clients.ActiveDirectory.AdalServiceException:  
AADSTS70002: Error validating credentials. AADSTS50054: Old password is used for authentication.

## Next steps
**Overview topics**

* [Azure AD Connect sync: Understand and customize synchronization](how-to-connect-sync-whatis.md)
* [Integrating your on-premises identities with Azure Active Directory](whatis-hybrid-identity.md)

