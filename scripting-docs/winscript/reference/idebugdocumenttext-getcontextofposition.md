---
title: 'Idebugdocumenttext:: GetContextOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetContextOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetContextOfPosition
ms.assetid: 86560853-d9b1-499a-a1b5-ea06aa1f1f5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6a35a85a6e4761e1bd0db67caafd0913e7e28a3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572144"
---
# <a name="idebugdocumenttextgetcontextofposition"></a>IDebugDocumentText::GetContextOfPosition
Belirtilen karakter konum aralığına karşılık gelen bir belge bağlamı nesnesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetContextOfPosition(  
   ULONG                    cCharacterPosition,  
   ULONG                    cNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cCharacterPosition`  
 'ndaki Karakter konumu aralığının başlangıç konumu.  
  
 `cNumChars`  
 'ndaki Aralıktaki karakter sayısı.  
  
 `ppsc`  
 dışı Belirtilen karakter konumu aralığına karşılık gelen belge bağlamı nesnesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, belirtilen karakter konum aralığına karşılık gelen bir belge bağlamı nesnesi oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugDocumentText Arabirimi](../../winscript/reference/idebugdocumenttext-interface.md)