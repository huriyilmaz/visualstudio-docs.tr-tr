---
title: 'Idebugdocumenttext:: GetPositionOfLine | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetPositionOfLine
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetPositionOfLine
ms.assetid: d1e6e81b-ddec-4a7c-9b6a-d199e3debfc2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adf4add99ac41440e6f4daa491b72166e97b5ba5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572107"
---
# <a name="idebugdocumenttextgetpositionofline"></a>IDebugDocumentText::GetPositionOfLine
Satırın ilk karakterine karşılık gelen karakter konumunu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetPositionOfLine(  
   ULONG   cLineNumber,  
   ULONG*  pcCharacterPosition  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cLineNumber`  
 'ndaki Satır numarası.  
  
 `pcCharacterPosition`  
 dışı Satır başı `cLineNumber` belge içindeki karakter konumu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir satırın ilk karakterine karşılık gelen karakter konumunu döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugDocumentText Arabirimi](../../winscript/reference/idebugdocumenttext-interface.md)