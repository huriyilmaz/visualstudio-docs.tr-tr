---
title: Kaynak Denetimi Eklentisi Mimarisi | Microsoft Docs
description: Kaynak denetimi eklentilerini uygulayarak ve Visual Studio IDE'ye kaynak denetimi desteği ekleme hakkında bilgi öğrenin.
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
ms.openlocfilehash: 3e77815e04604e4818afb8d3f81d1cfd14830fd89ab095dd24df92fb6e57331f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275222"
---
# <a name="source-control-plug-in-architecture"></a>Kaynak Denetimi Eklentisi Mimarisi
Tümleşik geliştirme ortamına (IDE) kaynak denetimi desteği eklemek için bir kaynak denetimi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eklentisi uygulayabilirsiniz. IDE, kaynak denetimi eklentisine API'sini kullanarak iyi tanımlanmış Kaynak Denetimi Plug-In bağlanır. IDE, araç çubuklarını ve menü komutlarını bir kullanıcı arabirimi (UI) sağlayarak kaynak denetim sisteminin sürüm denetimi özelliklerini ortaya çıkarır. Kaynak denetimi eklentisi, kaynak denetimi işlevselliğini uygulamaya almaktadır.

## <a name="source-control-plug-in-resources"></a>Kaynak Denetimi Eklentisi Kaynakları
 Kaynak Denetimi Eklentisi, sürüm oluşturma uygulamanızı oluşturmanıza ve IDE'ye bağlamanıza yardımcı olacak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynaklar sağlar. Kaynak Denetimi Eklentisi, IDE ile tümleştirilmesi için bir kaynak denetimi eklentisi tarafından uygulanması gereken API [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] belirtimlerini içerir. Ayrıca Kaynak Denetimi Eklentisi API'si ile uyumlu temel işlevlerin uygulanmasını gösteren bir iskelet kaynak denetimi eklentisi uygulayan bir kod örneği (C++ ile yazılmış) içerir.

 Kaynak Denetimi Eklentisi API'si belirtimi, Kaynak Denetimi Eklentisi API'sine uygun olarak uygulanan gerekli işlev kümesine sahip bir kaynak denetimi DLL'si oluşturursanız, tercih edersiniz herhangi bir kaynak denetim sisteminden faydalanmanızı sağlar.

## <a name="components"></a>Bileşenler
 Diyagramda Kaynak Denetim Bağdaştırıcısı Paketi, kullanıcının kaynak denetim işlemi isteğini kaynak denetim eklentisi tarafından desteklenen bir işlev çağrısına çeviren IDE'nin bileşenidir. Bunun olması için, IDE ve kaynak denetimi eklentisinin, bilgileri IDE ile eklenti arasında ileri ve geri aktaran etkili bir iletişim kutusu olması gerekir. Bu iletişim kutusunun olması için her ikisinin de aynı dili konuşmaları gerekir. Bu belgelerde özetlenen Kaynak Denetimi Eklentisi API'si, bu değişimin ortak sözlüğü olarak kullanılır.

 ![Kaynak Kodu Denetimi Mimarisi Diyagramı](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") VS ile kaynak denetimi eklentisi arasındaki etkileşimi gösteren Mimari Diyagramı

 Mimari diyagramında gösterildiği gibi, diyagramda VS kabuğu olarak etiketlenmiş olan kabuk, kullanıcının çalışma projelerini ve düzenleyiciler ve düzenleyiciler gibi ilişkili [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bileşenleri Çözüm Gezgini. Kaynak Denetim Bağdaştırıcısı Paketi, IDE ile kaynak denetimi eklentisi arasındaki etkileşimi ele almaktadır. Kaynak Denetim Bağdaştırıcısı Paketi kendi kaynak denetimi kullanıcı arabirimini sağlar. Bir kaynak denetimi işlemi başlatmak ve kapsamını tanımlamak için kullanıcının etkileşim kurduğu üst düzey kullanıcı arabirimidir.

 Kaynak denetimi eklentisinin kendi kullanıcı arabirimi olabilir ve bu da şekilde gösterildiği gibi iki bölümden oluşur. "Satıcı Kullanıcı Arabirimi" etiketli kutu, kaynak denetimi eklentisi oluşturucusu olarak sizin sağlanmış özel kullanıcı arabirimi öğelerini temsil eder. Bunlar, kullanıcı gelişmiş bir kaynak denetimi işlemi çağıran kaynak denetimi eklentisi tarafından doğrudan görüntülenir. "Yardımcı Kullanıcı Arabirimi" olarak etiketlenmiş kutu, IDE aracılığıyla dolaylı olarak çağrılan bir kaynak denetimi eklentisi kullanıcı arabirimi özellikleri kümesidir. Kaynak denetimi eklentisi, IDE tarafından sağlanan özel geri çağırma işlevleri aracılığıyla kullanıcı arabirimiyle ilgili iletileri IDE'ye iletir. Yardımcı kullanıcı arabirimi, IDE ile daha sorunsuz bir tümleştirmeyi  (genellikle Gelişmiş düğmesi kullanarak) kolaylaştırır ve böylece daha birleşik bir son kullanıcı deneyimi sağlar.

 Kaynak denetimi eklentisi, kabukta ve sonuç olarak IDE tarafından sağlanan Kaynak Denetim Bağdaştırıcısı Paketinde veya kaynak denetimi kullanıcı arabiriminde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] değişiklik yapmamalıdır. Son kullanıcı için tümleşik bir deneyime katkıda bulunan çeşitli Kaynak Denetimi Eklentisi API'si işlevlerinin uygulanması yoluyla sunulan esnekliği en üst düzeyde kullanmalıdır. Kaynak Denetimi Eklentisi API'si belgelerinin başvuru bölümünde bazı gelişmiş kaynak denetimi eklentisi özellikleriyle ilgili bilgiler yer almaktadır. Bu özelliklerden yararlanmak için kaynak denetimi eklentisinin başlatma sırasında IDE'ye gelişmiş özelliklerini bildirmiş olması ve her bir özellik için belirli gelişmiş işlevleri uygulaması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../../extensibility/source-control-plug-ins.md)
- [Sözlük](../../extensibility/source-control-plug-in-glossary.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
