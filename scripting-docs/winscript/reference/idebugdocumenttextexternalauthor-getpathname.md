---
title: 'Idebugdocumenttextexternalauthor:: GetPathName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetPathName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e876b41ce1bde4defffd11267c6665f9d57da077
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575961"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Belgenin tam yolunu ve dosya adını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbstrLongName`  
 dışı Tam yolu ve dosya adını içeren dize.  
  
 `pfIsOriginalFile`  
 dışı Yolun ve dosya adının özgün belgeye başvurmasını belirten Boole değeri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_FAIL`|Kaynak dosya oluşturulamıyor veya belirlenemiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, belgenin tam yolunu ve dosya adını döndürür.  
  
 @No__t_0 FALSE ise, `pbstrLongName` yol ve dosya adı yeni oluşturulan geçici bir dosyaya başvurur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugDocumentTextExternalAuthor Arabirimi](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)