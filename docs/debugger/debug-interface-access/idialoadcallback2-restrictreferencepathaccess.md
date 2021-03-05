---
description: . Pdb dosyasına aranmaya,. exe dosyasının bulunduğu yolda izin verilip verilmeyeceğini belirler.
title: 'IDiaLoadCallback2:: RestrictReferencePathAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0801cd36af23e3a4e3ff911494e00f9bd232a4a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157401"
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
. Pdb dosyasına aranmaya,. exe dosyasının bulunduğu yolda izin verilip verilmeyeceğini belirler.

## <a name="syntax"></a>Syntax

```C++
HRESULT RestrictReferencePathAccess();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `S_OK`. Exe dosyasının bulunduğu yoldaki bir. pdb dosyasını aramaya engel olan herhangi bir dönüş kodu.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
