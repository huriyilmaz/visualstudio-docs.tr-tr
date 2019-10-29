---
title: 'Iwebappdiagnosticssetup:: CreateObjectWithSiteAtWebApp | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 253b995c200566868ac9ccc06b259e0a152e1676
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984601"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Bu yöntem, kimliği `rclsid` `dwClsContext`kullanarak, kimliğini içine geçirdiğiniz sınıfı birlikte oluşturur. Bu, [IRemoteDebugApplication:: Createınstanceatapplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) çalışmasına benzer. bunun dışında, nesne `CreateObjectWithSiteAtWebApp` olması durumunda Web uygulamasının Kullanıcı arabirimi iş parçacığında zaman uyumsuz olarak oluşturulur. Sınıf KIMLIĞI tarafından belirtilen nesne [ıwebappdiagnosticsobjectınitialization arabirimini](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)uygulamalıdır. Nesne oluşturulduktan sonra, [ıwebappdiagnosticsobjectınitialization:: Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) , PDM hata ayıklama uygulamasına yönelik bir başvuru ve `CreateObjectWithSiteAtWebApp``hPassToObject` parametresi ile çağırılır. Bu yöntemi, [DuplicateHandle](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle)kullanarak kopyaladığınız anonim bir kanala yönelik bir tanıtıcı uygulamaya geçirmek için kullanabilirsiniz.  
  
> [!IMPORTANT]
> [Iwebappdiagnosticssetup ARABIRIMI](../../winscript/reference/iwebappdiagnosticssetup-interface.md) PDM v 11.0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `rclsid`  
 Oluşturulacak sınıfın sınıf KIMLIĞI.  
  
 `dwClsContext`  
 Kodun çalıştırılacağı bağlam. Çoğu durumda, CLSCTX_INPROC_SERVER olur.  
  
 `riid`  
 Kullanılmadı.  
  
 `hPassToObject`  
 Nesnesi [ıwebappdiagnosticsobjectınitialization arabirimini](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)UYGULUYORSA, UI iş parçacığında oluşturulduktan sonra nesnesine geçirilecek bir değer.