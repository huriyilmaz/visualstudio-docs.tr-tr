---
title: 'IDiaStackWalkHelper:: get_registerValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fb78b4cbdfa2130731e3847b1a3325ab4cb3eac
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464725"
---
# <a name="idiastackwalkhelperget_registervalue"></a>IDiaStackWalkHelper::get_registerValue
Bir kaydın değerini alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `index`

'ndaki Değerin hangi kayda alınacağını belirten [CV_HREG_e sabit](../../debugger/debug-interface-access/cv-hreg-e.md) listesi numaralandırmasından bir değer.

 `pRetVal`

dışı Kaydın geçerli değerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Parametrenin boyutuna rağmen `pRetVal` bir uygulama yalnızca kaydın normal olarak tuttuğu şeyi depolamalıdır. Örneğin, 8 bitlik bir kayıt yalnızca verilen değerin en düşük 8 bitini barındırır. Bu yöntemden döndürülen bu 8 bitlik değer 64-bit olarak genişletilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e Numaralandırması](../../debugger/debug-interface-access/cv-hreg-e.md)