---
title: 'Icriptnode:: CreateChildHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e024bb7d6a81b35994edddfe9e71666b0ee8df0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573598"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Bir `IScriptNode` alt örneği olarak bir kod oluşturma yöntemi ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszDefaultName`  
 'ndaki Kod oluşturma yöntemi ile ilişkilendirilecek varsayılan adın adresi.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] Konaktaki tam adı taşıyan tanımlayıcıların listesi.  
  
 `cpszNames`  
 'ndaki @No__t_0 parametresindeki tanımlayıcıların sayısı.  
  
 `pszEvent`  
 'ndaki Kod oluşturma yöntemi ile ilişkili olay adını tanımlayan arabellek adresi.  
  
 `pszDelimiter`  
 'ndaki Son betik blok sınırlayıcısı adresi. Ayrıştırma için, ana bilgisayar genellikle bir sınırlayıcı (örneğin, iki tek tırnak işareti) kullanır ve komut dosyası bloğunun sonunu algılar.  
  
 Sınırlayıcı, betik yazma altyapısı tarafından ön işleme etkinleştirilir. Örneğin, altyapı tek tırnak işaretini sınırlayıcı olarak kullanılmak üzere iki tek tırnak işaretiyle değiştirebilir. Motor, sınırlandırıcının nasıl kullanıldığını belirler.  
  
 Betik bloğunun sonunu tanımlamak için sınırlayıcı kullanılmazsa NULL olarak ayarlayın.  
  
 `ptiSignature`  
 'ndaki Bir işlev nesnesi için tür bilgileri.  
  
 `iMethodSignature`  
 'ndaki @No__t_0 parametresindeki işlevin dizini.  
  
 `isn`  
 'ndaki Üst öğe içindeki alt öğenin dizini.  
  
 `dwCookie`  
 'ndaki Girişi ana bilgisayar nesnesiyle ilişkilendirmek için kullanılan uygulama tanımlı bir değer.  
  
 `ppse`  
 dışı Alt örneğin `IScriptEntry` arabirimine bir işaretçi alan bir değişkenin adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir kod oluşturma yöntemi olay işleyicisini belirtir. Bu yöntem, bir Web sayfasını temsil eden bir `IScriptNode` nesnesi tarafından çağrılırsa bir kod oluşturma yöntemi oluşturur. Bu yöntem, diğer arabirimler tarafından çağrılırsa başarılı olmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Icriptnode arabirimi](../../winscript/reference/iscriptnode-interface.md)    
 [IScriptEntry Arabirimi](../../winscript/reference/iscriptentry-interface.md)