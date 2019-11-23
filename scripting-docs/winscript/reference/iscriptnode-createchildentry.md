---
title: 'Icriptnode:: CreateChildEntry | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c58ff83c43a1418e6fb7bd8945afa181af60c68a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573612"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Bir `IScriptEntry`alt örneği ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `isn`  
 'ndaki Üst öğe içindeki alt öğenin dizini.  
  
 `dwCookie`  
 'ndaki Alt girişi ana bilgisayar nesnesiyle ilişkilendirmek için kullanılan uygulama tanımlı bir değer.  
  
 `pszDelimiter`  
 'ndaki Son betik blok sınırlayıcısı adresi. Ayrıştırma için, ana bilgisayar genellikle bir sınırlayıcı (örneğin, iki tek tırnak işareti) kullanır ve komut dosyası bloğunun sonunu algılar.  
  
 Sınırlayıcı, betik yazma altyapısının ön işleme sağlamasına olanak sağlar. Örneğin, altyapı tek tırnak işaretini sınırlayıcı olarak kullanılmak üzere iki tek tırnak işaretiyle değiştirebilir. Motor, sınırlandırıcının nasıl kullanıldığını belirler.  
  
 Bir sınırlayıcı betik bloğunun sonunu işaretlemez ise NULL olarak ayarlayın.  
  
 `ppse`  
 dışı Alt örneğin `IScriptEntry` arabirimine bir işaretçi alan bir değişkenin adresi.  
  
 Bir Web sayfasını temsil eden `IScriptNode` nesneler için, bu parametre bir betik bloğunu belirten bir `IScriptEntry` örneği döndürür.  
  
 Bir betik bloğunu temsil eden `IScriptEntry` nesneler için, bu parametre bir işlev nesnesini belirten bir `IScriptEntry` örneği döndürür.  
  
 Bir işlev nesnesini temsil eden `IScriptEntry` nesneler için, bu yöntem başarısız olur.  
  
 `IScriptScriptlet` nesneler için bu yöntem başarısız olur.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IScriptNode` arabirimi bir Web sayfasını veya öğelerini temsil eder. `IScriptEntry` arabirimi (`IScriptNode`türetilen), bir betik bloğunu veya bir işlev nesnesini temsil eder. `IScriptScriptlet` arabirimi (`IScriptEntry`türetilen) bir olay işleyicisini temsil eder.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Icriptnode arabirimi](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry Arabirimi](../../winscript/reference/iscriptentry-interface.md)