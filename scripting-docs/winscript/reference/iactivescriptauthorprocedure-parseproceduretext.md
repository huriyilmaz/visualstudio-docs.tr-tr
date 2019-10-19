---
title: Iactivescriptauthorprocedure::P arseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11a34843f30274ec78f1652c5ed5cd4dbcf2884a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572823"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Kod yordamını ayrıştırır, kod yordamının metnini betik yazma altyapısına ekler ve kod yordamına karşılık gelen bir `IScriptEntry` nesnesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszCode`  
 'ndaki Ayrıştırılacak betik metni.  
  
 `pszFormalParams`  
 'ndaki Yordamın biçimsel parametre adlarının adresi. Parametre adları, betik yazma altyapısı için uygun sınırlayıcılarla ayrılmalıdır. Adlar parantez içine alınmalıdır.  
  
 `pszProcedureName`  
 'ndaki Ayrıştırılacak yordam adının adresi.  
  
 `pszItemName`  
 'ndaki @No__t_0 nesnesiyle ilişkili öğe adını içeren arabellek adresi.  
  
 `pszDelimiter`  
 'ndaki Son betik blok sınırlayıcısı adresi. @No__t_0 metin akışından ayrıştırıldığında, ana bilgisayar genellikle bir sınırlayıcı (örneğin, iki tek tırnak işareti) kullanır ve komut dosyası bloğunun sonunu algılar. Betik bloğunun sonunu işaretlemek için sınırlayıcı yoksa bu parametreyi NULL olarak ayarlayın.  
  
 `dwCookie`  
 'ndaki Yeni `IScriptEntry` nesnesiyle ilişkili uygulama tanımlı bir değer.  
  
 `dwFlags`  
 'ndaki Kullanılmıyor.  
  
 `pdispFor`  
 'ndaki Kullanılmıyor.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Geçerli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] altyapısı bu yöntemi uygulamıyor.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptAuthorProcedure Arabirimi](../../winscript/reference/iactivescriptauthorprocedure-interface.md)