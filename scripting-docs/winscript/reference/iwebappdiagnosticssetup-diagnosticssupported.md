---
title: Iwebappdiagnosticssetup::D ıagnokıssupported | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd27e7c8759054fa2d7d67858d8d006fa9c9a152
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984578"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Bu uygulamada tanılamaların desteklenip desteklenmediğini belirler. [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) , bu arabirimi uygulayan nesne üzerinde null olmayan bir değerle çağrılırsa, [diagnosticssupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) `true`döndürür. Aksi takdirde, `false` döndürür ve [ıwebappdiagnosticssetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) Fail öğesine çağrı yapılır.  
  
> [!IMPORTANT]
> [Iwebappdiagnosticssetup ARABIRIMI](../../winscript/reference/iwebappdiagnosticssetup-interface.md) PDM v 11.0 ve üzeri tarafından uygulanır. Activdbg100 içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) , bu arabirimi uygulayan nesne üzerinde null olmayan bir değerle çağrılırsa, [diagnosticssupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) `true`döndürür. Aksi takdirde, `false`döndürür ve [ıwebappdiagnosticssetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) Fail öğesine çağrı yapılır.