---
title: 'Iactivescriptauthor:: AddScriptlet | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a349a848f282e6b3a228c7b17009e0261801be5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577982"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Kök düzeyi `IScriptNode` nesnenin alt öğesi olarak bir kod kod oluşturma yöntemi ekler. Konakta, kod oluşturma yöntemi tam adının yalnızca iki düzeyi olmasına izin verilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszDefaultName`  
 'ndaki Kod oluşturma yöntemi ile ilişkilendirilecek varsayılan adın adresi.  
  
 `pszCode`  
 'ndaki Kod oluşturma yöntemi metninin adresi.  
  
 `pszItemName`  
 'ndaki Konaktaki tam kod oluşturma yöntemi adının üst düzey tanımlayıcısının arabellek adresi.  
  
 `pszSubItemName`  
 'ndaki Konaktaki tam kod oluşturma yöntemi adının ikinci düzey tanımlayıcısının arabellek adresi. Ad yalnızca bir düzey içeriyorsa NULL olarak ayarlanır.  
  
 `pszEventName`  
 'ndaki Kod oluşturma yöntemi olay işleyicisi olduğu olay adını içeren bir arabelleğin adresi.  
  
 `pszDelimiter`  
 'ndaki Son betik blok sınırlayıcısı adresi. @No__t_0 metin akışından ayrıştırıldığında, ana bilgisayar genellikle bir sınırlayıcı (örneğin, iki tek tırnak işareti) kullanır ve komut dosyası bloğunun sonunu algılar. Bir sınırlayıcı betik bloğunun sonunu işaretlemez ise bu parametreyi NULL olarak ayarlayın.  
  
 `dwCookie`  
 'ndaki Kod oluşturma yöntemi bir konak nesnesiyle ilişkilendirmek için kullanılan uygulama tanımlı bir değer.  
  
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