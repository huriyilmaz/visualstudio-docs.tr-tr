---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89c5b6418e832dd145837e579cfded3f47022e00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466604"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Bu küme içindeki özellikler için bir Numaralandırıcı alır.

## <a name="syntax"></a>Söz dizimi

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