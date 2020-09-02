---
title: 'IDiaSymbol:: get_unmodifiedType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_unmodifiedType method
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6ab6bd7fc756e648955efa6db5ba9c186952d84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64806582"
---
# <a name="idiasymbolget_unmodifiedtype"></a>IDiaSymbol::get_unmodifiedType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu sembolün orijinal türünü alır. [SymTagEnum numaralandırması](../../debugger/debug-interface-access/symtagenum.md) bir türe ayarlandığında kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_unmodifiedType(   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı Bu sembolün orijinal türünü temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.  
  
> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.  
  
## <a name="remarks"></a>Açıklamalar  
 Geçerli tür, döndürülen özgün türün bir değişimdir. Bir simgenin özgün türü, ilk olarak simgenin türü ve sonra özgün tür için döndürülen tür için bir alan tarafından belirlenebilir. Bazı sembollerin özgün türde değiştirilmiş bir türü olamayacağını unutmayın.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: dia2. h  
  
 Kitaplık: diaguid. lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
