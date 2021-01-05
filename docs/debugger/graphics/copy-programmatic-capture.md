---
title: Kopyala (Programlı yakalama) | Microsoft Docs
description: Etkin grafik günlüğü (. vsglog) dosyasının içeriğini yeni bir dosyaya kopyalamak için VsgDbg sınıfının Copy yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 126b1d7a2fa9064a343e7eadbe83dd1eeecccb83
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727850"
---
# <a name="copy-programmatic-capture"></a>Kopyalama (Programlı Yakalama)
Etkin grafik günlüğü (. vsglog) dosyasının içeriğini yeni bir dosyaya kopyalar.

## <a name="syntax"></a>Sözdizimi

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Parametreler
 `szNewVSGLog` Yeni grafik günlük dosyasının dosya adı.

## <a name="remarks"></a>Açıklamalar
 Grafik bilgilerini yeni bir dosyaya kopyalamak için bazı grafik bilgilerini zaten yakalamış olmanız gerekir; Aksi takdirde hiçbir şey olmaz.