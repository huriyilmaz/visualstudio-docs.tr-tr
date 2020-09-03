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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72734813"
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