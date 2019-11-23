---
title: 'Iremotedebugapplication110:: SetDebuggerOptions | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::SetDebuggerOptions
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7168a4ef8ec70368c0ff691ba1f721275f9d65d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577418"
---
# <a name="iremotedebugapplication110setdebuggeroptions"></a>IRemoteDebugApplication110::SetDebuggerOptions
Hata ayıklayıcı seçeneklerini güncelleştirmek için çağırılır. Bu yöntem [IRemoteDebugApplication:: ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)öğesinden sonra çağrılmalıdır. [IRemoteDebugApplication::D ısconnectdebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) yöntemi otomatik olarak varsayılan seçeneklere sıfırlanır. Varsayılan seçenek 0 ' dır (SDO_NONE).  
  
> [!IMPORTANT]
> [IRemoteDebugApplication ARABIRIMI](../../winscript/reference/iremotedebugapplication-interface.md) PDM v 11.0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetDebuggerOptions(        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,        [in] enum SCRIPT_DEBUGGER_OPTIONS value    );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `mask`  
 [SCRIPT_DEBUGGER_OPTIONS numaralandırma](../../winscript/reference/script-debugger-options-enumeration.md) maskesi.  
  
 `value`  
 [SCRIPT_DEBUGGER_OPTIONS numaralandırma](../../winscript/reference/script-debugger-options-enumeration.md) değeri.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IRemoteDebugApplication arabirimi](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 Arabirimi](../../winscript/reference/iremotedebugapplication110-interface.md)