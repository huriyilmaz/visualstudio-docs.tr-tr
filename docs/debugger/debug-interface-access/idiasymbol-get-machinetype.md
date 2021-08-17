---
description: Hedef CPU 'nun türünü alır.
title: 'IDiaSymbol:: get_machineType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_machineType method
ms.assetid: 30870b10-6f32-45c6-a0d7-020dea707710
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9af5d5b0b3dd4563daf88637f2fbf3c94eb32ccc09341156bc175375925a3622
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121436414"
---
# <a name="idiasymbolget_machinetype"></a>IDiaSymbol::get_machineType
Hedef CPU 'nun türünü alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_machineType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Hedef CPU türünü belirten [IMAGE_FILE_MACHINE_ sabitlerinden](/windows/desktop/SysInfo/image-file-machine-constants) bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IMAGE_FILE_MACHINE_ sabitleri](/windows/desktop/SysInfo/image-file-machine-constants) 
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
