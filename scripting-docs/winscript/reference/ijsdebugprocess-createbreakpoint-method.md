---
title: 'Ijsdebugprocess:: CreateBreakPoint yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b0a4d595a11dc54829c467a0aace9601042fa08
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575098"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint Yöntemi
Kesme noktasını belirtilen belge konumunda ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `documentId`  
 'ndaki Idebugdocumenttext işaretçisi.  
  
 `characterOffset`  
 'ndaki Dosyanın başından itibaren karakter boşluğu.  
  
 `characterCount`  
 'ndaki Kesme noktasının ekleneceği belge metninin uzunluğu.  
  
 `isEnabled`  
 'ndaki Kesme noktasının etkinleştirilip etkinleştirilmeyeceğini belirtir.  
  
 `ppDebugBreakPoint`  
 dışı Oluşturulan kesme noktasını temsil eden nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsDebugProcess Arabirimi](../../winscript/reference/ijsdebugprocess-interface.md)