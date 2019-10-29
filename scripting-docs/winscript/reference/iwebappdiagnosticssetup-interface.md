---
title: Iwebappdiagnosticssetup arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e9bb3905da6227b978bc27b96493500f8d6d2ff
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984536"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup Arabirimi
Bu arabirim, hata ayıklanan işlemde COM nesneleri oluşturmak ve Web tanılamayı etkinleştirmek için bir PDM hata ayıklama uygulaması tarafından uygulanır. PDM hata ayıklama uygulama nesnesi [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite)uygularsa, Internet Explorer oluşturulduktan sonra, bir [denetiminden IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127(v=vs.85))başvurusunda geçiş yapıldıktan sonra [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) çağırır. Bir WWA uygulaması [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) çağırır ve bunun yerine WWA arabirim ıwebapplicationhost içinde geçirir. [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) null olmayan bir değerle çağrılırsa [ıwebappdiagnosticssetup::D ıagnohossupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) doğru döndürür. Aksi takdirde, false döndürür ve [ıwebappdiagnosticssetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) Fail öğesine çağrı yapılır.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsSetup`, PDM v 11.0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirim aşağıdaki yöntemleri sunar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Belirtilen filtreyle gizlenen metin belgelerini alır.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Belirtilen belgenin bu düğümün alt düğümlerinden birine ait olup olmadığını belirler.|