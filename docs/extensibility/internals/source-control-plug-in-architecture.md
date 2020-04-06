---
title: Kaynak Kontrol Plug-in Mimarisi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f549ad2c4ee456860a08fbf20ccda813934a8582
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705105"
---
# <a name="source-control-plug-in-architecture"></a>Kaynak Denetimi Eklentisi Mimarisi
Bir kaynak denetim eklentisi uygulayarak ve takarak tümleşik geliştirme ortamına [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) kaynak denetimi desteği ekleyebilirsiniz. IDE, iyi tanımlanmış Kaynak Kontrol Eklentisi API'si aracılığıyla kaynak kontrol eklentisine bağlanır. IDE, araç çubukları ve menü komutlarından oluşan bir kullanıcı arabirimi (UI) sağlayarak kaynak denetim sisteminin sürüm denetim özelliklerini ortaya çıkarır. Kaynak denetimi eklentisi kaynak denetimi işlevini uygular.

## <a name="source-control-plug-in-resources"></a>Kaynak Kontrol Eklentisi Kaynakları
 Kaynak Denetimi Eklentisi, sürüm uygulamanızın oluşturulmasına ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE'ye bağlanmasına yardımcı olacak kaynaklar sağlar. Kaynak Denetim Eklentisi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE'ye entegre edilebilmek için bir kaynak denetim eklentisi tarafından uygulanması gereken API belirtimini içerir. Ayrıca, Kaynak Denetim Eklentisi API ile uyumlu temel işlevlerin uygulanmasını gösteren bir iskelet kaynak kontrol eklentisi uygulayan bir kod örneği (C++'da yazılır) içerir.

 Kaynak Denetimi Eklentisi API belirtimi, Kaynak Denetimi Eklentisi API'sına uygun olarak uygulanan gerekli fonksiyonlar kümesiyle bir kaynak denetimi DLL oluşturursanız, istediğiniz kaynak kontrol sisteminden yararlanmanızı sağlar.

## <a name="components"></a>Bileşenler
 Diyagramdaki Kaynak Denetim Bağdaştırıcı Paketi, kullanıcının kaynak denetim işlemi isteğini kaynak denetim eklentisi tarafından desteklenen bir işlev çağrısına çeviren IDE bileşenidir. Bunun olabilmesi için, IDE ve kaynak denetim eklentisinin Bilgileri IDE ile eklenti arasında ileri geri aktaran etkili bir iletişim kutusuna sahip olması gerekir. Bu iletişimin gerçekleşmesi için her ikisinin de aynı dili konuşması gerekir. Bu belgede özetlenen Kaynak Denetimi Eklentisi API'si bu değişim için ortak kelime dağarcığıdır.

 ![Kaynak Kodu Kontrol Mimarisi Diyagramı](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") VS ve kaynak kontrol eklentisi arasındaki etkileşimi gösteren Mimari Diyagramı

 Mimari diyagramda gösterildiği gibi, diyagramda VS kabuğu olarak etiketlenen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kabuk, kullanıcının çalışma projelerini ve düzenleyiciler ve Çözüm Gezgini gibi ilişkili bileşenleri barındırıyor. Kaynak Kontrol Bağdaştırıcı Paketi, IDE ile kaynak kontrol eklentisi arasındaki etkileşimi işler. Kaynak Kontrol Bağdaştırıcı Paketi kendi kaynak denetimi kullanıcı kullanıcı aracını sağlar. Bir kaynak denetim işleminin kapsamını başlatmak ve tanımlamak için kullanıcının etkileşimde olduğu üst düzey kullanıcı dır.

 Kaynak denetim eklentisi, şekilde gösterildiği gibi iki bölümden oluşabilecek kendi ui'sine sahip olabilir. "Satıcı AraBirimi" etiketli kutu, kaynak denetimi eklentisi oluşturucusu olarak sağladığınız özel kullanıcı arabirimi öğelerini temsil eder. Bunlar, kullanıcı gelişmiş bir kaynak denetim işlemi çağırdığında doğrudan kaynak denetim eklentisi tarafından görüntülenir. "Yardımcı UI" etiketli kutu, IDE aracılığıyla dolaylı olarak çağrılan bir kaynak denetimi eklentisi ui özelliği kümesidir. Kaynak denetimi eklentisi, IDE tarafından sağlanan özel geri arama işlevleri aracılığıyla UI ile ilgili iletileri IDE'ye geçirir. Yardımcı Kullanıcı Aracı, IDE ile daha sorunsuz bir tümleştirmeyi (genellikle **Gelişmiş** bir düğme nin kullanımı yoluyla) kolaylaştırır ve böylece daha birleşik bir son kullanıcı deneyimi sağlar.

 Bir kaynak denetim eklentisi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kabukta ve sonuç olarak Kaynak Denetim Bağdaştırıcı Paketi'nde veya IDE tarafından sağlanan kaynak denetimi ui'sinde değişiklik yapamaz. Son kullanıcı için tümleşik bir deneyime katkıda bulunan çeşitli Kaynak Denetimi Eklentisi API işlevlerinin uygulanması yoluyla sunulan esnekliği maksimum düzeyde kullanmalıdır. Kaynak Denetimi Eklentisi API belgelerinin başvuru bölümü, bazı gelişmiş kaynak denetimi eklentisi özelliklerine ilişkin bilgileri içerir. Bu özelliklerden yararlanmak için kaynak denetim eklentisinin başlatma sırasında gelişmiş yeteneklerini IDE'ye bildirmesi ve her yetenek için belirli gelişmiş işlevleri uygulaması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../../extensibility/source-control-plug-ins.md)
- [Sözlük](../../extensibility/source-control-plug-in-glossary.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
