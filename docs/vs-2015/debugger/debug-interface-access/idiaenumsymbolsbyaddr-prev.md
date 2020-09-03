---
title: IDiaEnumSymbolsByAddr::P Rev | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7a5debb0ffccffed4077c367d5b008a2a2a7cc2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189636"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Önceki sembolleri sırasıyla adrese göre alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 celt  
 'ndaki Numaralandırıcıda alınacak olan simgelerin sayısı.  
  
 rgelt  
 dışı İstenen sembolleri temsil eden [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesneleriyle doldurulacak bir dizi.  
  
 Pceltfettiz  
 dışı Getirilen Numaralandırıcı içindeki simgelerin sayısını döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Önceki semboller yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, Numaralandırıcı konumunu getirilen öğe sayısına göre güncelleştirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
