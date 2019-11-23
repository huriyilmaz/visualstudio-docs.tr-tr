---
title: 'Iactivescriptdebug:: EnumCodeContextsOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::EnumCodeContextsOfPosition
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aedfe5d40d8f4086e30f3a62c070b8ccd5ef2388
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572774"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Bir akıllı ana bilgisayar tarafından `IDebugDocumentContext::EnumCodeContexts` metodunu devretmek için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwSourceContext`  
 'ndaki `IActiveScriptParse::ParseScriptText` veya `IActiveScriptParse::AddScriptlet`için belirtilen kaynak bağlamı.  
  
 `uCharacterOffset`  
 'ndaki Betik metninin başlangıcına göre karakter boşluğu.  
  
 `uNumChars`  
 'ndaki Bu bağlamdaki karakterlerin sayısı.  
  
 `ppescc`  
 dışı Belirtilen aralıktaki kod bağlamlarının numaralandırıcısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Akıllı konaklar, `IDebugDocumentContext::EnumCodeContexts` metodunu atamak için bu yöntemi kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptdebug arabirimi](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)