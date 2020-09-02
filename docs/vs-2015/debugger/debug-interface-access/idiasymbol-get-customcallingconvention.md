---
title: 'IDiaSymbol:: get_customCallingConvention | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_customCallingConvention method
ms.assetid: 0aa97951-f7e1-4fa5-a87f-2920460c122d
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b56203f2d0bfb2e7c20720b595cdde6b92aa987
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64834383"
---
# <a name="idiasymbolget_customcallingconvention"></a>IDiaSymbol::get_customCallingConvention
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İşlevin özel bir çağırma kuralına sahip olup olmadığını belirten bir bayrak alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_customCallingConvention(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pFlag`  
 dışı `TRUE` İşlevin özel bir çağırma kuralına sahip olup olmadığını döndürür; Aksi takdirde, `FALSE` işlevinin bilinen bir çağırma kuralı vardır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.  
  
> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|Gereksinim|Description|  
|-----------------|-----------------|  
|Üst bilgi|dia2. h|  
|Sürüm:|DIA SDK v 8.0|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
