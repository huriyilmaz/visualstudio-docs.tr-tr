---
title: 'Iremotedebugapplication110:: GetMainThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetMainThread
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff99c43f633da8454eb5fa32463886877e06ed72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574113"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)çağıran konaklar için ana iş parçacığını döndürür, aksı takdirde E_FAIL döndürür.  
  
> [!IMPORTANT]
> [IRemoteDebugApplication ARABIRIMI](../../winscript/reference/iremotedebugapplication-interface.md) PDM v 11.0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppThread`  
 dışı Ana [ıremotedebugapplicationthread arabirimi](../../winscript/reference/iremotedebugapplicationthread-interface.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IRemoteDebugApplication arabirimi](../../winscript/reference/iremotedebugapplication-interface.md)    
 [IRemoteDebugApplication110 Arabirimi](../../winscript/reference/iremotedebugapplication110-interface.md)