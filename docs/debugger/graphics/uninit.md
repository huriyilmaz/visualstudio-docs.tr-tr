---
title: Başlatma geri | Microsoft Docs
description: Grafik günlük dosyasını sonlandırmak ve kapatmak ve günlük kaynaklarını boşaltmak için VsgDbg öğesinin UnInit () yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7cead2d7c1c98e4f481e6057c9ab79c8dc908683
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905015"
---
# <a name="uninit"></a>UnInit
Grafik günlük dosyasını sonlandırır, kapatır ve uygulama grafik bilgilerini etkin bir şekilde kaydederken kullanılan kaynakları serbest bırakır.

## <a name="syntax"></a>Syntax

```C++
void UnInit();
```

## <a name="remarks"></a>Açıklamalar
 `UnInit` , sınıfının bir örneği yok edildiğinde otomatik olarak çağrılır `VsgDbg` . Örnek, `VsgDbg` grafik bilgilerini etkin bir şekilde kaydetmediği takdirde bu bir etkiye sahip değildir.

 `UnInit`Sınıfının bir örneği üzerinde çağrıldıktan sonra `VsgDbg` , çağırarak çağırarak ve sonlandırıldığında yeni bir grafik günlük dosyası oluşturulabilir `Init` `UnInit` . `VsgDbg`Birkaç bağımsız grafik günlük dosyası oluşturmak için aynı örneği kullanmak istediğiniz kadar bu adı tekrarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Dengeleyici](init.md)