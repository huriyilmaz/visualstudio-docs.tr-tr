---
title: 'IDiaSymbol:: Findsymbolsbyrvaforivatorpointertag | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee1aea023124fb8277fd13cf341a63fca92c37cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149869"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Karşılık gelen bir etiket değeri verildiğinde, bu yöntem, belirtilen bir göreli sanal adresteki bu saplama işlevinde bulunan simgelerin bir listesini döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `tagValue`  
 'ndaki Pointee sembol kayıtlarının bulunduğu işaretçi etiketi değeri.  
  
 `rva`  
 'ndaki Belirtilen etiket değeriyle pointee değişkenine karşılık gelen sembolleri filtrelemek için kullanılan RVA.  
  
 `ppResult`  
 dışı `IDiaEnumSymbols` Sonuçla başlatılan arabirim işaretçisine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemi yalnızca `IDiaSymbol` bir Hızlandırıcı saplama işlevine karşılık gelen bir arabirimde çağırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
