---
description: Belirtilen etiket değerinin üst Hızlandırıcı saplama işlevinde karşılık geldiği değişken için bir sembol numaralandırması döndürür.
title: 'IDiaSession:: Findsymbolsforivatorpointertag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4d1a177cd1c36a2e51f846bf60edfbef875a51df
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158931"
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
Belirtilen etiket değerinin üst Hızlandırıcı saplama işlevinde karşılık geldiği değişken için bir sembol numaralandırması döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findSymbolsForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `parent`

'ndaki Aranmak üzere Hızlandırıcı saplama işlevine karşılık gelen bir IDiaSymbol.

 `tagValue`

'ndaki İşaretçi etiketi değeri.

 `ppResult`

dışı `IDiaEnumSymbols` Sonuçla başlatılan arabirim işaretçisine yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
