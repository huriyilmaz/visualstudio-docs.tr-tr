---
description: Bu küme içindeki özellikler için bir Numaralandırıcı alır.
title: 'IDiaPropertyStorage:: Enum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7458a0cd509567b52ab14b4489f5fded2f187882
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129050"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Bu küme içindeki özellikler için bir Numaralandırıcı alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Enum ( 
   IEnumSTATPROPSTG** ppenum
);
```

#### <a name="parameters"></a>Parametreler
 `ppenum`

dışı `IEnumSTATPROPSTG` Özelliklerin bir listesini temsil eden bir nesne döndürür (Microsoft. VisualStudio. OLE. Interop ad alanında).

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
