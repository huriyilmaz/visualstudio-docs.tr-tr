---
title: 'IDiaSymbol:: get_textureSlot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 166a1a3a-2e10-4baa-ace1-9104b56185ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 050e2b4db8a29ab0b80774f4e135624109729405
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461818"
---
# <a name="idiasymbolget_textureslot"></a>IDiaSymbol::get_textureSlot
Doku yuvasını alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_textureSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `DWORD`Doku yuvasını tutan bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)