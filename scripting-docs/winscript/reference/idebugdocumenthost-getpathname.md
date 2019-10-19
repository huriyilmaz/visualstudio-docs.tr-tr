---
title: 'Idebugbelgethost:: GetPathName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetPathName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetPathName
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33ebcde4cf1db28e199f13fae720374bd1b64763
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569285"
---
# <a name="idebugdocumenthostgetpathname"></a>IDebugDocumentHost::GetPathName
Belgenin kaynak dosyasının tam yolunu ve dosya adını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbstrLongName`  
 dışı Uzun adı içeren bir dize.  
  
 `pfIsOriginalFile`  
 dışı @No__t_0 belge için özgün dosyaya başvuruyorsa true, aksi durumda false olan bayrak.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_FAIL`|Kaynak dosyası oluşturulamaz veya belirlenemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, belgenin kaynak dosyasının tam yolunu ve dosya adını döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugDocumentHost Arabirimi](../../winscript/reference/idebugdocumenthost-interface.md)