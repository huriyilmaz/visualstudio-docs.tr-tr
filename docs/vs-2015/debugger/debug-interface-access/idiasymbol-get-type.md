---
title: 'IDiaSymbol:: get_type | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9bec7cdbf0641bbd1bba1e70c2f21ec232a18e6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787557"
---
# <a name="idiasymbolget_type"></a>IDiaSymbol::get_type
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu sembolün türünü temsil eden simgeyi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_type (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı Bu sembolün türünü temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.  
  
> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir sembolün türünü öğrenmek için, bu yöntemi çağırmanız ve elde edilen [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesini incelemeniz gerekir. Bir simgenin bir türe sahip olmadığı için mümkün olduğunu unutmayın. Örneğin, bir yapının adında hiçbir tür yoktur, ancak alt sembolleri olabilir (Bu alt öğeleri incelemek için [IDiaSymbol:: findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md) metodunu kullanın).  
  
## <a name="example"></a>Örnek  
  
```cpp#  
IDiaSymbol*         pType;  
CComPtr<IDiaSymbol> pBaseType;  
if (SUCCEEDED(pType->get_type( &pBaseType ))) {  
    BasicType btBaseType;  
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {  
        // Do something with basic type.  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
