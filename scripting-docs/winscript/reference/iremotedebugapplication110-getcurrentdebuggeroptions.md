---
title: 'Iremotedebugapplication110:: GetCurrentDebuggerOptions | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetCurrentDebuggerOptions
ms.assetid: a6e9cae1-e8f3-4d62-b133-52e9ca12ba7a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ae042a5d4d1c1ee350b328fdc5a9b7420d9928
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577440"
---
# <a name="iremotedebugapplication110getcurrentdebuggeroptions"></a>IRemoteDebugApplication110::GetCurrentDebuggerOptions
Şu anda etkin olan seçenek kümesini döndürür.  
  
> [!IMPORTANT]
> [IRemoteDebugApplication ARABIRIMI](../../winscript/reference/iremotedebugapplication-interface.md) PDM v 11.0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCurrentDebuggerOptions([out] enum SCRIPT_DEBUGGER_OPTIONS* pCurrentOptions);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pCurrentOptions`  
 dışı Geçerli seçenekler.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IRemoteDebugApplication arabirimi](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 Arabirimi](../../winscript/reference/iremotedebugapplication110-interface.md)