---
title: 'IDiaSymbol:: get_intro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df8930d620f6199ecde4d6d921d5b969204f92e6
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "64830323"
---
# <a name="idiasymbolget_intro"></a>IDiaSymbol::get_intro
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İşlevin bir sanal işlev olduğunu belirten bir bayrak alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_intro (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı `TRUE` İşlevin giriş sanal olup olmadığını döndürür; Aksi takdirde, döndürür `FALSE` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.  
  
> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.  
  
## <a name="example"></a>Örnek  
  
```cpp#  
class A {  
   virtual int f1();  
}  
class B : public A {  
   int f1();  
}  
```  
  
 Hem hem de `A::f1` `B::f1` sanal işlevlerdir, ancak `A::f1` giriş sanal.  
  
## <a name="requirements"></a>Gereksinimler  
  
|Gereksinim|Açıklama|  
|-----------------|-----------------|  
|Üst bilgi|dia2. h|  
|Sürüm:|DIA SDK v 7.0|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
