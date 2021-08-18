---
description: Bu işaretçinin bir sembol değerini temel alarak kullanıp kullanmadığını belirtir.
title: 'IDiaSymbol:: get_isPointerBasedOnSymbolValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 577c8011-9269-4373-8577-b4822a983724
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 241e5c27f92b6a21ee444e3f2c0c06c17b3048de
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036090"
---
# <a name="idiasymbolget_ispointerbasedonsymbolvalue"></a>IDiaSymbol::get_isPointerBasedOnSymbolValue
`this`İşaretçinin bir sembol değerini temel alarak çalışıp çalışmadığını belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isPointerBasedOnSymbolValue(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `BOOL` İşaretçisinin bir sembol değerine dayalı olup olmadığını belirten bir işaretçisi `this` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
