---
title: 'IDiaSymbol:: get_undecoratedName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedName method
ms.assetid: e49edf25-a51d-4787-bd5b-2bf5af827c8c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d6a40bb739ea68dbc08c3dc3b3f98271261e6cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64791207"
---
# <a name="idiasymbolget_undecoratedname"></a>IDiaSymbol::get_undecoratedName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

C++ ile düzenlenmiş veya bağlantı adı için, açıklanmamalıdır adı alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_undecoratedName (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı C++ ile düzenlenmiş bir ad için, açıklanmunadı döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.  
  
> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
