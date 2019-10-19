---
title: Iactivescriptauthor::P arseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 90d5ab0fa700ed29b5fb37b1c48617cedec871b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576145"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Betik metnini ayrıştırır, metni betik yazma altyapısına ekler ve betik bloğuna karşılık gelen bir `IScriptEntry` nesnesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszCode`  
 'ndaki Ayrıştırılacak betik metni.  
  
 `pszItemName`  
 'ndaki Betik bloğuyla ilişkili öğe adını içeren arabellek adresi.  
  
 `pszDelimiter`  
 'ndaki Son betik blok sınırlayıcısı adresi. @No__t_0 metin akışından ayrıştırıldığında, ana bilgisayar genellikle bir sınırlayıcı (örneğin, iki tek tırnak işareti) kullanır ve komut dosyası bloğunun sonunu algılar. Betik bloğunun sonunu tanımlamak için sınırlayıcı yoksa bu parametreyi NULL olarak ayarlayın.  
  
 `dwCookie`  
 'ndaki Yeni `IScriptEntry` nesnesiyle ilişkili uygulama tanımlı bir değer.  
  
 `dwFlags`  
 'ndaki Kullanılmıyor.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptAuthor Arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)