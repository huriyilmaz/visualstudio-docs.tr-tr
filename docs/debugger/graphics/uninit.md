---
title: Başlatma geri | Microsoft Docs
description: Grafik günlük dosyasını sonlandırmak ve kapatmak ve günlük kaynaklarını boşaltmak için VsgDbg öğesinin UnInit () yöntemini kullanın.
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
ms.openlocfilehash: 031d14efcf7985e70f7276ec1f6475b2e02adf7c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626445"
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