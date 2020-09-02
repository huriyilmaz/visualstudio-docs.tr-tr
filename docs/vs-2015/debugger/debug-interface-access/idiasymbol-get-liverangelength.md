---
title: 'IDiaSymbol:: get_liveRangeLength | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeLength
ms.assetid: ffcce3cc-085c-44eb-8145-46e3819c54f9
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33f56615334b7d33516c6c967f165dac3942b5f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64825239"
---
# <a name="idiasymbolget_liverangelength"></a>IDiaSymbol::get_liveRangeLength
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yerel simgenin geçerli olduğu adres aralığının uzunluğunu döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_liveRangeLength (   
   ULONGLONG* length  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `length`  
 dışı Adres aralığının uzunluğunu döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
> [!NOTE]
> Döndürülen bir hata kodu, simgenin canlı Aralık bilgilerine sahip olmadığı anlamına gelir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: dia2. h  
  
 Kitaplık: diaguid. lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
