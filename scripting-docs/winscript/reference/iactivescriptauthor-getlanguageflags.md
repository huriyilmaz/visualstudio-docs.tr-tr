---
title: 'Iactivescriptauthor:: GetLanguageFlags | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68da16513050bd87642be2c96212a330a0916608
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576198"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Dil bilgisini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pgrfasa`  
 dışı Dil bilgisi içeren bayraklar. Aşağıdaki değerlerin bir birleşimi olabilir:  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|Fasapreferınternalhandler|0x0001|Dil, uygulama yerine betik yazma altyapısı tarafından betik olay işleyicisini oluşturmayı tercih eder.|  
|Fasasupportınternalhandler|0x0002|Dil, betik yazma altyapısı tarafından oluşturulan komut dosyası olay işleyicilerini destekler.|  
|fasaCaseSensitive|0x0004|Betik dili, büyük/küçük harfe duyarlıdır.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Betik yazma altyapısı olay işleyicilerini yönetirse, uygulamanız bir `IScriptEntry` nesnesinden `CreateChildHandler` çağırmalıdır. Bu, olay işleyicisine karşılık gelen bir `IScriptScriptlet` nesnesi oluşturur. Motor Ayrıca betik girdisine bir olay işleyicisi ekler. Olay işleyicisi, belirtilen imza bilgilerini içeren boş bir işlevdir.  
  
 Uygulamanız olay işleyicilerini yönetirse, bir olay işleyicisi kod oluşturma yöntemi temsil eden bir `IScriptNode` nesnesinden `CreateChildHandler` çağırmalıdır. Bu, kod oluşturma yöntemi olay işleyicisi ile ilişkili bir `IScriptScriptlet` nesnesi oluşturur. Uygulamanın Ayrıca yeni veya var olan bir `IScriptEntry` nesnesine bir olay işleyicisi olarak boş bir işlev eklemesi gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptAuthor Arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)