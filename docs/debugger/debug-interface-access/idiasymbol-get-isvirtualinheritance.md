---
description: Bu işaretçinin sanal devralmaya sahip bir veri üyesine işaret edip ede olmadığını belirtir.
title: IDiaSymbol::get_isVirtualInheritance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 72906b92-dd4a-42e3-9b24-b77628fa48c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d57d647855c30eee350cf088ecf35f68f6c15d2a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052232"
---
# <a name="idiasymbolget_isvirtualinheritance"></a>IDiaSymbol::get_isVirtualInheritance
İşaretçinin sanal `this` devralma ile bir veri üyesine işaret edip ede olmadığını belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isVirtualInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] İşaretçinin `BOOL` sanal devralmaya sahip bir veri `this` üyesine işaret edip olmadığını belirten bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
