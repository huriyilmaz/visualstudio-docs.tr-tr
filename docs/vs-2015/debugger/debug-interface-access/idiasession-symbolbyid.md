---
title: 'IDiaSession:: symbolById | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ac409edcee7657e724822d1a72737c3142d8d93e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150200"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir sembolü benzersiz tanımlayıcısına göre alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `id`  
 'ndaki Benzersiz tanımlayıcı.  
  
 `ppSymbol`  
 dışı Alınan simgeyi temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtilen tanımlayıcı, tüm sembolleri benzersiz hale getirmek için DIA SDK tarafından dahili olarak kullanılan benzersiz bir değerdir.  
  
 Bu yöntem, örneğin, başka bir simgenin türünü temsil eden simgeyi almak için kullanılabilir (örneğe bakın).  
  
## <a name="example"></a>Örnek  
 Bu örnek, başka bir simgenin türünü temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) alır. Bu örnek, oturumunda yönteminin nasıl kullanılacağını gösterir `symbolById` . Daha basit bir yaklaşım, tür sembolünü doğrudan almak için [IDiaSymbol:: get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) yöntemini çağırmalıdır.  
  
```cpp#  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
