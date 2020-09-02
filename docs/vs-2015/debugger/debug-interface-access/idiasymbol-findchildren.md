---
title: 'IDiaSymbol:: findChildren | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a09a62a2e6b94dbccda3afce4bdd286270149c15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150038"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Simgenin alt öğelerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `symtag`  
 'ndaki [SymTagEnum numaralandırmasında](../../debugger/debug-interface-access/symtagenum.md)tanımlandığı şekilde alınacak alt öğelerin sembol etiketlerini belirtir. `SymTagNull`Tüm alt öğelerin alınması için olarak ayarlayın.  
  
 `name`  
 'ndaki Alınacak alt öğelerin adını belirtir. `NULL`Tüm alt öğelerin alınması için olarak ayarlayın.  
  
 `compareFlags`  
 'ndaki Ad eşleştirme için uygulanan karşılaştırma seçeneklerini belirtir. [NameSearchOptions numaralandırma](../../debugger/debug-interface-access/namesearchoptions.md) numaralandırmasındaki değerler tek başına veya birlikte kullanılabilir.  
  
 `ppResult`  
 dışı Alınan alt simgelerin listesini içeren bir [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) nesnesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`Simgenin en az bir alt öğesi bulunursa veya `S_FALSE` alt öğe bulunmazsa öğesini döndürür; Aksi takdirde bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, ilk parametre olarak bu sembolle [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) yöntemini çağırmaya benzer.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum numaralandırması](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions Numaralandırması](../../debugger/debug-interface-access/namesearchoptions.md)
