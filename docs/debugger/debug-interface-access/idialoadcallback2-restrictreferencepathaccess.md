---
title: 'IDiaLoadCallback2:: RestrictReferencePathAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3406052f4d5466b5b7f52a1da3490d35bbb0508f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742990"
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
. Pdb dosyasına aranmaya,. exe dosyasının bulunduğu yolda izin verilip verilmeyeceğini belirler.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT RestrictReferencePathAccess();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 . Exe dosyasının bulunduğu yoldaki bir. pdb dosyasına bakmasını engellemek için `S_OK` dışındaki herhangi bir dönüş kodu.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)