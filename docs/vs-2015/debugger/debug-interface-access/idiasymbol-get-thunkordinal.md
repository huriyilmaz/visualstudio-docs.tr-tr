---
title: 'IDiaSymbol:: get_thunkOrdinal | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 540eb49b215d06127a47df1defc436a0a307aa6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64784294"
---
# <a name="idiasymbolget_thunkordinal"></a>IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir işlevin dönüştürücü türünü alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı Bir işlevin dönüştürücü türünü belirten [THUNK_ORDINAL sabit](../../debugger/debug-interface-access/thunk-ordinal.md) listesi numaralandırmasından bir değer döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.  
  
> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu özellik yalnızca sembol bir [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değeri olarak sembolü ise geçerlidir `SymTagThunk` .  
  
 "Dönüştürücü", 32 bitlik bir bellek adres alanı (düz adres alanı olarak da bilinir) ve 16 bit adres alanı (bölümlenmiş adres alanı olarak bilinir) arasında dönüştürme yapan bir kod parçasıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [THUNK_ORDINAL numaralandırması](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
