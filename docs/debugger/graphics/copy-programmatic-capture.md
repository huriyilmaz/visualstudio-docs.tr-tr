---
title: Kopyala (Programlı yakalama) | Microsoft Docs
description: Etkin grafik günlüğü (. vsglog) dosyasının içeriğini yeni bir dosyaya kopyalamak için VsgDbg sınıfının Copy yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 26a9aff077e3cb7cda6e809546f850fc6a9fc754
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626456"
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