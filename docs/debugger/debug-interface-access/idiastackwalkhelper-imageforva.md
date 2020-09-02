---
title: 'IDiaStackWalkHelper:: ımageforva | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f28af62a4e5eaa89e92db533bf461dbecaf039d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464718"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Yürütülebilir dosyanın bellek alanında bir sanal adres verildiğinde, bir yürütülebilir dosyanın belleğindeki görüntüsünün başlangıcını döndürür.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT imageForVA(
   ULONGLONG  vaContext,
   ULONGLONG *pvaImageStart
);
```

#### <a name="parameters"></a>Parametreler
 `vaContext`

'ndaki Yürütülebilir dosyanın alanında bir yerde yer alan sanal adres.

 `pvaImageStart`

dışı Yürütülebilir dosyanın başlangıç sanal adresini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)