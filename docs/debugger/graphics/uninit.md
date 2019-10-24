---
title: Başlatma geri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef809b646a0af58e46b8c68dc5a8cf7633692bcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734813"
---
# <a name="uninit"></a>UnInit
Grafik günlük dosyasını sonlandırır, kapatır ve uygulama grafik bilgilerini etkin bir şekilde kaydederken kullanılan kaynakları serbest bırakır.

## <a name="syntax"></a>Sözdizimi

```C++
void UnInit();
```

## <a name="remarks"></a>Açıklamalar
 `VsgDbg` sınıfının bir örneği yok edildiğinde `UnInit` otomatik olarak çağrılır. @No__t_0 örneği grafik bilgilerini etkin bir şekilde kaydetmediği takdirde, bu, hiçbir etkiye sahip değildir.

 @No__t_0 `VsgDbg` sınıfının bir örneğinde çağrıldıktan sonra, `UnInit` çağırarak `Init` ve sonlandırıldığında çağırarak yeni bir grafik günlük dosyası oluşturulabilir. Birkaç bağımsız grafik günlük dosyası oluşturmak için aynı `VsgDbg` örneğini kullanmak istediğiniz kadar bunu yineleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Init](init.md)