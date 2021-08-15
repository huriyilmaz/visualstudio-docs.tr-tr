---
title: UnInit | Microsoft Docs
description: VsgDbg'nin UnInit() yöntemini kullanarak grafik günlük dosyasını son olarak ve kapatarak günlük kaynaklarını serbest bırakabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0534ef85ec1bebb9483e4d815447476004394efa0dfe61dc27b2ba404209c562
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239863"
---
# <a name="uninit"></a>UnInit
Grafik günlüğü dosyasını son olarak hazırlar, kapatır ve uygulama grafik bilgilerini etkin bir şekilde kaydederken kullanılan kaynakları serbest bıraktırır.

## <a name="syntax"></a>Syntax

```C++
void UnInit();
```

## <a name="remarks"></a>Açıklamalar
 `UnInit` sınıfın bir örneği yok edilirse otomatik `VsgDbg` olarak çağrılır. Örnek `VsgDbg` grafik bilgilerini etkin bir şekilde kaydedemse, bunun bir etkisi yoktur.

 sınıfının bir örneğinde çağrıldıktan sonra, çağrılarak yeni bir grafik günlüğü dosyası oluşturulabilir ve `UnInit` `VsgDbg` `Init` çağrılarak son hale `UnInit` getirildi. Birkaç bağımsız grafik günlüğü dosyası oluşturmak için aynı örneği kullanmak `VsgDbg` istediğiniz kadar tekrarlayın.

## <a name="see-also"></a>Ayrıca bkz.
- [ınit](init.md)