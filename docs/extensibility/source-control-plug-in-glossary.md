---
title: Kaynak denetimi eklentisi sözlüğü | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 672a96c31137a52f3bd4a8c826cef1b19406790b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719581"
---
# <a name="source-control-plug-in-glossary"></a>Kaynak Denetimi Eklentisi Sözlüğü
Aşağıdaki faydalı hüküm ve tanımlar, kaynak denetimi eklentisi SDK belgeleriyle ilgilidir.

## <a name="definitions"></a>Tanımlar
 İade etme Kullanıcı çalışma kopyasında değişiklik yaptığında, kullanıcının değişiklikleri çalışma kopyasından merkezi kaynak denetimi deposuna gönderebilmesi gerekir. Bu, dosyanın diğer kullanıcılar tarafından kullanılabilen yeni bir düzeltmesini oluşturur. Bu işleme iade adı verilir.

 Depodan bir çalışma kopyası isteme işlemini kullanıma alın ve bu depoyu, onu değiştirme amacınızı bildirerek bilgilendirin. Çalışma kopyası, projenin durumunu kullanıma alındığı andan itibaren yansıtır.

 İstemci, kaynak kodu denetim sistemini kullanan bir program. Bu belgelerin amacına yönelik olarak, Visual Studio IDE 'dir.

 Bir kaynak denetim işlemi gerçekleştirildiğinde bir kullanıcının düzeltmeye iliştireme yaptığı değişiklikleri açıklayan bir ileti ekleyin.

 İki kullanıcı aynı dosyanın aynı bölgesindeki değişiklikleri iade etmek için bir durum çakışması. Genellikle, bir birleştirme gerçekleştirilmelidir.

 Dizin bir istemci tarafı yerel klasörü, dizin olarak adlandırılır. Bu, kullanıcının aslında değişiklik yaptığı kopyasıdır. Belirli bir projenin birçok çalışma kopyası olabilir; genellikle her geliştiricinin kendi kopyası vardır.

 Get işlemi, kullanıcının çalışma kopyasını depo kopyasıyla güncel hale getirir. Bir kullanıma almanın aksine, Kullanıcı yalnızca en son kopyaya ihtiyaç duymadığında ancak hiçbir değişiklik yapmadan bir alma işlemi gerçekleştirilir.

 Geçmiş genellikle kaynak denetim deposunda yapılan tüm kullanıma alma işlemleri, iadeler, güncelleştirmeler, Etiketler ve sürümlerin bir özetidir.

 IDE genellikle Visual Studio tümleşik geliştirme ortamına başvurur. Ancak, kaynak denetimi eklentisi API 'sini tanıyan diğer istemci ortamlarına de başvurabilir.

 Önceki dosyalardaki tüm özellikleri ekleyen yeni bir dosya oluşturmak için iki veya daha fazla kaynak kodu dosyasının birleştirileceği işlemi birleştirin. Bu kavram, iki veya daha fazla geliştiricinin dosyalarda eşzamanlı olarak çalıştığı sürüm denetiminde hayati öneme sahiptir.

 Proje kaynak denetim klasörü genellikle proje olarak adlandırılır. Bu, Visual Studio 'daki proje veya çözümlerle hiçbir ilişkiye sahip değildir.

 Kaynak denetimi eklentisi API 'sini uygulayarak kaynak denetimi işlevselliği sağlayan bir DLL eklentisi.

 Kaynak denetim sisteminin bir projenin tam değişiklik geçmişini sakladığı ana kopyayı depoya koyun. Her projenin tam olarak bir deposu vardır.

 Bir dosyanın veya dosya kümesinin geçmişinde yürütülen değişikliği düzeltme. Bir düzeltme, sürekli değişen bir projede bir anlık görüntüdür.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../extensibility/source-control-plug-ins.md)