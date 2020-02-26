---
title: WriteContextTLogs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5c0793cc6d9f11cd1074c5cd0091687b154c069
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579463"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
Geçerli bağlam için günlük dosyalarını yazar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parametreler
[in] `intermediateDirectory`

 İzleme günlüğünün depolayabileceği dizin.

[in] `tlogRootName`

 Günlük dosyası adının kök adı.

## <a name="return-value"></a>Dönüş değeri
 İzleme bağlamı oluşturulduysa, **başarılı** biti ayarlanmış bir **HRESULT** .

## <a name="requirements"></a>Gereksinimler
 **Üstbilgi:** *FileTracker. h*

## <a name="see-also"></a>Ayrıca bkz.
- [WriteAllTLogs](../msbuild/writealltlogs.md)