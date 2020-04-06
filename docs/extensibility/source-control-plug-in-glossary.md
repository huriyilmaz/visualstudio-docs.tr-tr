---
title: Kaynak Kontrol Eklentisi Sözlüğü | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3835561eb63fa2a4a71174732c07ecd73f1df5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699903"
---
# <a name="source-control-plug-in-glossary"></a>Kaynak Denetimi Eklentisi Sözlüğü
Aşağıdaki yararlı terimler ve tanımlar Kaynak Denetimi Eklentisi SDK belgeleriyle ilgilidir.

## <a name="definitions"></a>Tanımlar
 İade Bir kullanıcı çalışan bir kopyada değişiklik yaptığında, kullanıcının çalışma kopyasındaki değişiklikleri merkezi kaynak denetim deposuna göndermesi gerekir. Bu, diğer kullanıcılar tarafından kullanılabilen dosyanın yeni bir revizyonunu oluşturur. Bu işleme iade denir.

 Ödeme Depodan çalışan bir kopya talep etme ve onu değiştirme niyetinizin deposunu bilgilendirme eylemi. Çalışan bir kopya, kullanıma alındıktan sonra projenin durumunu yansıtır.

 İstemci Kaynak kodu denetim sistemini kullanan bir program. Bu dokümantasyon un amacı Visual Studio IDE'dir.

 Yorum Kaynak denetim işlemi gerçekleştirilirken kullanıcının düzeltmeye ekebileceği değişiklikleri açıklayan ileti.

 Çakışma İki kullanıcı aynı dosyanın aynı bölgesinde değişiklikleri iade etmeye çalıştığınızda bir durum. Genellikle, birbirleştirme gerçekleştirilmelidir.

 Dizin Bir istemci tarafı yerel klasörü bir dizin olarak adlandırılır. Bu, kullanıcının gerçekten değişiklik yaptığı kopyadır. Belirli bir projenin birçok çalışma kopyası olabilir; genellikle her geliştiricinin kendi kopyası vardır.

 Get A işlemi, kullanıcının çalışan kopyasını depo kopyasıyla güncel bir şekilde getirir. Ödemenin aksine, kullanıcı nın yalnızca en son kopyaya ihtiyacı olduğunda ancak hiçbir değişiklik yapmayı planladığında bir alış gerçekleştirilir.

 Geçmiş Genellikle tüm ödeme, denetim, güncelleştirme, etiket ve kaynak denetim deposunda yapılan sürümlerin bir özetidir.

 IDE genellikle Visual Studio Entegre Geliştirme Ortamı anlamına gelir. Ancak, Kaynak Denetimi Eklentisi API'sini tanıyan diğer istemci ortamlarına da başvurabilir.

 İki veya daha fazla kaynak kodu dosyasının biraraya getirilerek önceki dosyalardaki tüm özellikleri içeren yeni bir dosya oluşturma işlemi birleştirin. Bu kavram, iki veya daha fazla geliştiricinin dosyalar üzerinde aynı anda çalıştığı sürüm denetiminde hayati önem taşır.

 Project A kaynak denetim klasörü genellikle proje olarak adlandırılır. Bunun Visual Studio'daki projeler veya çözümlerle herhangi bir ilişkisi yoktur.

 Kaynak Denetimi Eklentisi API'sini uygulayarak kaynak denetimi işlevselliği sağlayan Plug-in A DLL.

 Depo Kaynak denetim sisteminin projenin tam revizyon geçmişini depoladığı ana kopya. Her projenin tam olarak bir deposu vardır.

 Düzeltme Bir dosya nın veya dosya kümesinin geçmişinde yapılan bir değişiklik. Revizyon, sürekli değişen bir projedeki anlık görüntüdür.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../extensibility/source-control-plug-ins.md)
