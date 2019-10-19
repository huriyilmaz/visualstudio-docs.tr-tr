---
title: 'IActiveScriptSiteDebug32:: GetDocumentContextFromPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 7acbe2a5741fa94ac42470a85803d1720e0a8fa1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574843"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
@No__t_0 temsilci seçmek için dil altyapısı tarafından kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwSourceContext`  
 'ndaki @No__t_0 veya `AddScriptlet` için belirtilen kaynak içerik.  
  
 `uCharacterOffset`  
 'ndaki Betik bloğunun veya kod oluşturma yöntemi başlangıcına göre karakter boşluğu.  
  
 `uNumChars`  
 'ndaki Bu bağlamdaki karakterlerin sayısı.  
  
 `ppsc`  
 dışı Bu karakter konumu aralığına karşılık gelen belge bağlamı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Dil motorları `IDebugCodeContext::GetSourceContext` atamak için bu yöntemi kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSiteDebug32 Arabirimi](../../winscript/reference/iactivescriptsitedebug32-interface.md)