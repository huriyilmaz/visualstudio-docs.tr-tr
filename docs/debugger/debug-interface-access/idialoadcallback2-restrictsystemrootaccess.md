---
description: Sistem kök dizininde. pdb dosyalarına yönelik arama yapılmasına izin verilip verilmeyeceğini belirler.
title: 'IDiaLoadCallback2:: RestrictSystemRootAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictSystemRootAccess method
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2aed03fceee4b69a6b30cce8bd2257f98cff961b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161725"
---
# <a name="idialoadcallback2restrictsystemrootaccess"></a>IDiaLoadCallback2::RestrictSystemRootAccess
Sistem kök dizininde. pdb dosyalarına yönelik arama yapılmasına izin verilip verilmeyeceğini belirler.

## <a name="syntax"></a>Syntax

```C++
HRESULT RestrictSystemRootAccess();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dışında herhangi bir dönüş kodu `S_OK` ,. pdb dosyaları için sistem kökünü aramayı önler.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
