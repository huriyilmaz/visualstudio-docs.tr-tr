---
title: Kaynak denetimi eklentisi mimarisi | Microsoft Docs
description: kaynak denetimi eklentisini uygulayarak ve ekleyerek Visual Studio ıde 'sine kaynak denetimi desteğinin nasıl ekleneceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8a8a53a9e4c11b9a0a268221bd7ab068b7904409
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159106"
---
# <a name="source-control-plug-in-architecture"></a>Kaynak Denetimi Eklentisi Mimarisi
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kaynak denetimi eklentisini uygulayarak ve ekleyerek tümleşik geliştirme ortamına (IDE) kaynak denetimi desteği ekleyebilirsiniz. IDE, kaynak denetimi eklentisine, iyi tanımlanmış kaynak denetimi Plug-In API 'SI aracılığıyla bağlanır. IDE, araç çubukları ve menü komutlarından oluşan bir kullanıcı arabirimi (UI) sağlayarak kaynak denetim sisteminin sürüm denetim özelliklerini kullanıma sunar. Kaynak denetimi eklentisi, kaynak denetimi işlevini uygular.

## <a name="source-control-plug-in-resources"></a>Kaynak denetimi eklentisi kaynakları
 Kaynak denetimi eklentisi, sürüm oluşturma uygulamanızı oluşturmaya ve IDE 'ye bağlamaya yardımcı olmak için kaynak sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Kaynak denetimi eklentisi, IDE ile tümleştirilebilmesi için bir kaynak denetimi eklentisi tarafından uygulanması gereken API belirtimini içerir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Ayrıca, kaynak denetimi eklentisi API 'siyle uyumlu işlevlerin uygulanmasını gösteren bir iskelet kaynak denetimi eklentisi uygulayan bir kod örneği (C++ dilinde yazılmıştır) de bulunur.

 Kaynak denetimi eklentisi API 'si belirtimi, kaynak denetimi eklentisi API 'sine uygun olarak uygulanan gerekli işlevler kümesiyle bir kaynak denetimi DLL 'SI oluşturursanız, tercih ettiğiniz herhangi bir kaynak denetimi sisteminden yararlanmanızı sağlar.

## <a name="components"></a>Bileşenler
 Diyagramdaki kaynak denetim bağdaştırıcısı paketi, kullanıcının kaynak denetim işlemi isteğini kaynak denetimi eklentisi tarafından desteklenen bir işlev çağrısına çeviren IDE 'nin bileşenidir. Bunun gerçekleşmesi için IDE ve kaynak denetimi eklentisinin, IDE ve eklenti arasında bilgileri geri ve ileri geçiren etkin bir iletişim kutusu olmalıdır. Bu iletişim kutusunun gerçekleşmesi için, her ikisi de aynı dili konuşmalıdır. Bu belgede özetlenen kaynak denetimi eklentisi API 'SI, bu Exchange için ortak bir sözlük.

 ![Kaynak kodu denetim mimarisi diyagramı](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") VS ve kaynak denetimi eklentisi arasındaki etkileşimi gösteren mimari diyagramı

 Mimari diyagramında gösterildiği gibi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DIYAGRAMDA vs kabuğu olarak etiketlenmiş olan kabuk, kullanıcının çalışma projelerini ve düzenleyici ve Çözüm Gezgini gibi ilişkili bileşenleri barındırır. Kaynak denetim bağdaştırıcısı paketi IDE ve kaynak denetimi eklentisi arasındaki etkileşimi işler. Kaynak denetim bağdaştırıcısı paketi kendi kaynak denetimi kullanıcı arabirimini sağlar. Bu, kullanıcının bir kaynak denetimi işleminin kapsamını başlatmak ve tanımlamak için etkileşimde bulunduğu en üst düzey Kullanıcı arabirimindedir.

 Kaynak denetimi eklentisi kendi Kullanıcı arabirimine sahip olabilir ve bu, şekilde gösterildiği gibi iki bölümden oluşabilir. "Satıcı Kullanıcı arabirimi" etiketli kutu, kaynak denetimi eklentisi Oluşturucu olarak sağladığınız özel kullanıcı arabirimi öğelerini temsil eder. Bunlar, Kullanıcı Gelişmiş bir kaynak denetimi işlemini çağırdığında doğrudan kaynak denetimi eklentisi tarafından görüntülenir. "Yardımcı UI" etiketli kutu, IDE aracılığıyla dolaylı olarak çağrılan bir kaynak denetimi eklentisi Kullanıcı arabirimi özellikleri kümesidir. Kaynak denetimi eklentisi, IDE tarafından sunulan özel geri çağırma işlevleri aracılığıyla UI ile ilgili iletileri IDE 'ye geçirir. Yardımcı Kullanıcı arabirimi IDE ile daha sorunsuz bir tümleştirme sağlar (genellikle **Gelişmiş** bir düğme kullanılarak) ve bu sayede daha birleştirilmiş bir son kullanıcı deneyimi sağlar.

 Kaynak denetimi eklentisi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kabukta değişiklik yapamaz ve sonuç olarak kaynak denetim bağdaştırıcı paketine ya da IDE tarafından sağlanmış kaynak denetimi kullanıcı arabirimine sahip olamaz. Son Kullanıcı için tümleşik bir deneyime katkıda bulunan çeşitli kaynak denetimi eklentisi API işlevlerinin uygulanmasıyla sunulan esnekliği en fazla kullanması gerekir. Kaynak denetimi eklentisi API 'SI belgelerinin başvuru bölümü, bazı gelişmiş kaynak denetimi eklentisi özellikleri için bilgiler içerir. Bu özelliklerden yararlanmak için, kaynak denetimi eklentisinin başlatma sırasında IDE 'ye gelişmiş yeteneklerini bildirmesi ve her bir özellik için belirli gelişmiş işlevleri uygulaması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../../extensibility/source-control-plug-ins.md)
- [Sözlük](../../extensibility/source-control-plug-in-glossary.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
