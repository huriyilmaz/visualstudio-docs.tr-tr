---
title: 'IActiveScriptErrorDebug110:: GetExceptionThrownKind | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110::QueryIsFirstChance
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d50ef1dfa3492fdc43a5010b624dae296c692722
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575050"
---
# <a name="iactivescripterrordebug110getexceptionthrownkind"></a>IActiveScriptErrorDebug110::GetExceptionThrownKind
Oluşan özel durumun türünü gösteren bir değeri döndürür.  
  
> [!IMPORTANT]
> [IActiveScriptErrorDebug110 ARABIRIMI](../../winscript/reference/iactivescripterrordebug110-interface.md) PDM sürüm 11,0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pExceptionKind`  
 dışı Oluşturulan özel durum türü (örneğin, birinci şans veya işlenmemiş), bir [SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND numaralandırma](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md) numaralandırması değeri tarafından temsil edilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptErrorDebug110 Arabirimi](../../winscript/reference/iactivescripterrordebug110-interface.md)