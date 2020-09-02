---
title: 'IDiaSymbol:: get_hasSEH | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 72e8d428df4796c34c5ac20447e7bf8121f259d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703776"
---
# <a name="idiasymbolget_hasseh"></a>IDiaSymbol::get_hasSEH
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İşlevin [yapılandırılmış özel durum işleme (C/C++)](https://msdn.microsoft.com/library/dd3b647d-c269-43a8-aab9-ad1458712976) içerip içermediğini belirten bir bayrak alır (örneğin, __try/ \_ _Except blokları).  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_hasSEH(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pFlag`  
 dışı `TRUE` İşlevin yapılandırılmış özel durum işleme blokları varsa döndürür; Aksi takdirde, döndürür `FALSE` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.  
  
> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|Gereksinim|Description|  
|-----------------|-----------------|  
|Üst bilgi|dia2. h|  
|Sürüm:|DIA SDK v 8.0|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Yapılandırılmış Özel Durum İşleme (C/C++)](https://msdn.microsoft.com/library/dd3b647d-c269-43a8-aab9-ad1458712976)
