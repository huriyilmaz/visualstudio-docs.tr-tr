---
title: 'IActiveScriptSiteDebug32:: GetDocumentContextFromPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b43b16f46cc62b6c70460d79c194b5e0d2cfede0
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835283"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Temsilci seçmek için dil motoru tarafından kullanılır `IDebugCodeContext::GetSourceContext` .  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Veya için belirtilen kaynak içerik `ParseScriptText` `AddScriptlet` .  
  
 `uCharacterOffset`  
 'ndaki Betik bloğunun veya kod oluşturma yöntemi başlangıcına göre karakter boşluğu.  
  
 `uNumChars`  
 'ndaki Bu bağlamdaki karakterlerin sayısı.  
  
 `ppsc`  
 dışı Bu karakter konumu aralığına karşılık gelen belge bağlamı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi döndürür `HRESULT` . Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Description|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Dil motorları atamak için bu yöntemi kullanır `IDebugCodeContext::GetSourceContext` .  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSiteDebug32 Arabirimi](../../winscript/reference/iactivescriptsitedebug32-interface.md)