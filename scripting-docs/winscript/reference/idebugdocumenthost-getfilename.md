---
title: 'Idebugbelgethost:: GetFileName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetFileName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetFileName
ms.assetid: b814a848-8a3d-468d-9282-c5c0354b22a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ff2ad2e4ab419f1e503da072aaa550f3cb7cf0e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569396"
---
# <a name="idebugdocumenthostgetfilename"></a>IDebugDocumentHost::GetFileName
Yol bilgisi olmayan belgenin adını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbstrShortName`  
 dışı Belgenin kısa adını içeren bir dize.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, yol bilgisi olmadan belgenin kısa adını döndürür. Kısa ad genellikle farklı **Kaydet...** iletişim kutusu gibi durumlarda kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugDocumentHost Arabirimi](../../winscript/reference/idebugdocumenthost-interface.md)