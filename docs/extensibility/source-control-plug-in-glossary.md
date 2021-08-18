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
ms.openlocfilehash: bf9753900bcccaf92cd1813103ad41173355c2c3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049473"
---
# <a name="source-control-plug-in-glossary"></a>Kaynak Denetimi Eklentisi Sözlüğü
Aşağıdaki yararlı terimler ve tanımlar Kaynak Denetimi Eklentisi SDK belgeleriyle ilgilidir.

## <a name="definitions"></a>Tanımlar
 Kullanıcı çalışan bir kopyada değişiklik yaparsa, kullanıcının değişiklikleri çalışan kopyadan merkezi kaynak denetim deposuna göndermesi gerekir. Bu, dosyanın diğer kullanıcılar tarafından kullanılabilen yeni bir düzeltmesi oluşturur. Bu işleme iade adı verilen bir işlemdir.

 Depodan çalışan bir kopya isteği oluşturma ve depoyu değiştirme amacınızı bildirme eylemini kontrol edin. Çalışma kopyası, kullanıma alınmış olan andan itibaren projenin durumunu yansıtıyor.

 İstemci Kaynak kodu denetim sistemini kullanan bir program. Bu belgelerin amacı, Visual Studio IDE'dir.

 Açıklama: Kaynak denetimi işlemi gerçekleştirilecek bir kullanıcının düzeltmeye ek olarak ekley yaptığı değişiklikleri açıklayan bir ileti.

 Çakışma İki kullanıcı aynı dosyanın aynı bölgesinde yapılan değişiklikleri iade etmeye çalışma durumu. Genellikle bir birleştirme gerçekleştirin.

 Dizin İstemci tarafı yerel klasörü, dizin olarak adlandırılır. Bu, kullanıcının gerçekten değişiklik yaptığınız kopyadır. Bir projenin çok sayıda çalışan kopyası olabilir; genellikle her geliştiricinin kendi kopyası vardır.

 Get A get işlemi, kullanıcının çalışma kopyasını depo kopyasıyla güncel olarak getirir. Kullanımdan farklı olarak, kullanıcının yalnızca en son kopyaya ihtiyacı olduğunda ancak değişiklik yapma amacında olduğunda bir alma işlemi gerçekleştirilir.

 Geçmiş Genellikle kaynak denetim deposunda yapılan tüm iadelerin, iadelerin, güncelleştirmelerin, etiketlerin ve yayınların özetidir.

 IDE Genel olarak tümleşik Visual Studio ortamını ifade eder. Ancak, Kaynak Denetimi Eklentisi API'sini tanıyan diğer istemci ortamlarını da ifade eder.

 Birleştirme Önceki dosyalardan tüm özellikleri içeren yeni bir dosya oluşturmak için iki veya daha fazla kaynak kod dosyasının birleştirildi olduğu işlem. Bu kavram, iki veya daha fazla geliştiricinin dosyalar üzerinde eşzamanlı olarak çalışa bir sürüm denetiminde yaşamsal önem taşır.

 Project Kaynak denetim klasörü genellikle proje olarak adlandırılır. Bunun projelerle veya çözümlerle herhangi bir ilişkisi Visual Studio.

 Eklenti Kaynak Denetimi Eklentisi API'sini kullanarak kaynak denetimi işlevselliği sağlayan bir DLL.

 Depo Kaynak denetim sisteminin bir projenin tam düzeltme geçmişini depolayıp depolaması gereken ana kopya. Her projenin tam olarak bir deposu var.

 Düzeltme Bir dosya veya dosya kümesi geçmişinde kaydedilmiş bir değişiklik. Düzeltme, sürekli değişen bir projede yer alan anlık görüntülerdendir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../extensibility/source-control-plug-ins.md)
