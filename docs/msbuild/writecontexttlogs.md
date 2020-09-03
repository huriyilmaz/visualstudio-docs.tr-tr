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
ms.openlocfilehash: cf34ff63b00cf523ba9ef704f4417be4d5cdbf77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77630711"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs

Geçerli bağlam için günlük dosyalarını yazar.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parametreler

'ndaki `intermediateDirectory`

 İzleme günlüğünün depolayabileceği dizin.

'ndaki `tlogRootName`

 Günlük dosyası adının kök adı.

## <a name="return-value"></a>Döndürülen değer

 İzleme bağlamı oluşturulduysa, **başarılı** biti ayarlanmış bir **HRESULT** .

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker. h*

## <a name="see-also"></a>Ayrıca bkz.

- [WriteAllTLogs](../msbuild/writealltlogs.md)