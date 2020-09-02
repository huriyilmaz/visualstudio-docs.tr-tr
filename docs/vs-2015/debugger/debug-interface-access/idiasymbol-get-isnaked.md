---
title: 'IDiaSymbol:: get_isNaked | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isNaked method
ms.assetid: b16629dc-8e17-476b-9c7b-58e7277c61ed
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64989ca10416ab2ad9606c94b3f3bc977f60c5ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702355"
---
# <a name="idiasymbolget_isnaked"></a>IDiaSymbol::get_isNaked
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İşlevin [çıplak](https://msdn.microsoft.com/library/69723241-05e1-439b-868e-20a83a16ab6d) özniteliğe sahip olup olmadığını belirten bir bayrak alır (yani, işlevin derleyici tarafından eklenen giriş veya bitiş kodu yok).  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT get_isNaked(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pFlag`  
 dışı `TRUE` İşlevin özniteliğe sahip olup olmadığını döndürür `naked` ; Aksi takdirde, döndürür `FALSE` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.  
  
> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|Gereksinim|Description|  
|-----------------|-----------------|  
|Üst bilgi|dia2. h|  
|Sürüm:|DIA SDK v 8.0|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Naked Işlev çağrıları](https://msdn.microsoft.com/library/2a66847a-a43f-4541-a7be-c9f5f29b5fdb)
