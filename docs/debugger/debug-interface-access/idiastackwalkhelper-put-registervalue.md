---
description: IDiaStackWalkHelper::p ut_registerValue bir kaydın değerini ayarlar.
title: IDiaStackWalkHelper::p ut_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fdc66faea9537759e9754ce799339175db585673
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156827"
---
# <a name="idiastackwalkhelperput_registervalue"></a>IDiaStackWalkHelper::put_registerValue
Bir kaydın değerini ayarlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT put_registerValue ( 
   DWORD     index,
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parametreler
 `index`

'ndaki Yazılacak kaydı belirten [CV_HREG_e sabit listesi](../../debugger/debug-interface-access/cv-hreg-e.md) numaralandırmasından bir değer.

 `NewVal`

'ndaki Yeni kayıt değeri.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Değerin boyutuna rağmen bir uygulama yalnızca kaydın normal olarak tuttuğu şeyi depolamalıdır. Örneğin, 8 bitlik bir kayıt yalnızca verilen değerin en düşük 8 bitini tutacaktır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e Numaralandırması](../../debugger/debug-interface-access/cv-hreg-e.md)
