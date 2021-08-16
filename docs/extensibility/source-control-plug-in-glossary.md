---
title: Kaynak Denetimi Eklentisi Sözlüğü | Microsoft Docs
description: Bu makale, Kaynak Denetimi Eklentisi SDK'sı belgeleriyle ilgili yararlı terimler ve tanımlar içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 45d4c946e78a611d7e4837366fbbf618f317c775d7d362f2807ccd40d084b1c9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358954"
---
# <a name="source-control-plug-in-glossary"></a>Kaynak Denetimi Eklentisi Sözlüğü
Aşağıdaki yararlı terimler ve tanımlar Kaynak Denetimi Eklentisi SDK belgeleriyle ilgilidir.

## <a name="definitions"></a>Tanımlar
 Kullanıcı çalışan bir kopyada değişiklik yaparsa, kullanıcının değişiklikleri çalışan kopyadan merkezi kaynak denetim deposuna göndermesi gerekir. Bu, dosyanın diğer kullanıcılar tarafından kullanılabilen yeni bir düzeltmesi oluşturur. Bu işleme iade adı verilen bir işlemdir.

 Depodan çalışan bir kopya isteği oluşturma ve depoyu değiştirme amacınızı bildirme eylemini kontrol edin. Çalışma kopyası, kullanıma alınmış olan andan itibaren projenin durumunu yansıtıyor.

 İstemci Kaynak kodu denetim sistemini kullanan bir program. Bu belgelerin amacı, IDE'Visual Studio belgedir.

 Açıklama: Kaynak denetimi işlemi gerçekleştirilecek bir kullanıcının düzeltmeye ek olarak ekley yaptığı değişiklikleri açıklayan bir ileti.

 Çakışma İki kullanıcı aynı dosyanın aynı bölgesinde yapılan değişiklikleri iade etmeye çalışma durumu. Genellikle bir birleştirme gerçekleştirin.

 Dizin İstemci tarafı yerel klasörü, dizin olarak adlandırılır. Bu, kullanıcının gerçekten değişiklik yaptığınız kopyadır. Bir projenin çok sayıda çalışan kopyası olabilir; genellikle her geliştiricinin kendi kopyası vardır.

 Get A get işlemi, kullanıcının çalışma kopyasını depo kopyasıyla güncel olarak getirir. Kullanımdan farklı olarak, kullanıcı yalnızca en son kopyaya ihtiyaç olduğunda ancak değişiklik yapma amacında olduğunda bir alma işlemi gerçekleştirilir.

 Geçmiş Genellikle kaynak denetim deposunda yapılan tüm iadelerin, iadelerin, güncelleştirmelerin, etiketlerin ve yayınların özetidir.

 IDE Genel olarak tümleşik Visual Studio ortamını ifade eder. Ancak, Kaynak Denetimi Eklentisi API'sini tanıyan diğer istemci ortamlarını da ifade eder.

 Birleştirme Önceki dosyalardan tüm özellikleri içeren yeni bir dosya oluşturmak için iki veya daha fazla kaynak kod dosyasının birleştirildi olduğu işlem. Bu kavram, iki veya daha fazla geliştiricinin dosyalar üzerinde eşzamanlı olarak çalışa bir sürüm denetiminde yaşamsal önem taşır.

 Project Kaynak denetim klasörü genellikle proje olarak adlandırılır. Bunun projelerle veya çözümlerle herhangi bir ilişkisi Visual Studio.

 Eklenti Kaynak Denetimi Eklentisi API'sini kullanarak kaynak denetimi işlevselliği sağlayan bir DLL.

 Depo Kaynak denetim sisteminin projenin tam düzeltme geçmişini depolayıp depolaması gereken ana kopya. Her projenin tam olarak bir deposu var.

 Düzeltme Bir dosya veya dosya kümesi geçmişinde kaydedilmiş bir değişiklik. Düzeltme, sürekli değişen bir projede yer alan anlık görüntülerdendir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../extensibility/source-control-plug-ins.md)
