---
title: 'Idebugdocumenttext:: GetSize | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetSize
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetSize
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef6f75b396dddec80fb2ae89c71f8579ce3c29b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572087"
---
# <a name="idebugdocumenttextgetsize"></a>IDebugDocumentText::GetSize
Belgedeki satır sayısını ve karakter sayısını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pcNumLines`  
 dışı Belgedeki satır sayısı. Bu parametre NULL ise, yöntem bir değer döndürmez.  
  
 `pcNumChars`  
 dışı Belgedeki karakter sayısı. Bu parametre NULL ise, yöntem bir değer döndürmez.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, belgedeki satır sayısını ve karakter sayısını döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugDocumentText Arabirimi](../../winscript/reference/idebugdocumenttext-interface.md)