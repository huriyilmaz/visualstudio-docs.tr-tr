---
title: Kaynak Denetimi Tümleştirmeye Genel Bakış | Microsoft Docs
description: 'Kaynak denetimi ile kaynak denetimi Visual Studio arasındaki farkları öğrenin: kaynak denetimi eklentisi ve VSPackage.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0682f1d25ed01e5b7b3261718b7e2c261110137a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042107"
---
# <a name="source-control-integration-overview"></a>Kaynak Denetimini Tümleştirmeye Genel Bakış
Bu bölümde, kaynak denetimiyle tümleşmenin iki Visual Studio karşılaştırıldı; bir kaynak denetimi Eklentisi ve kaynak denetimi çözümü sağlayan ve yeni kaynak denetimi özelliklerini vurgulayan bir VSPackage. Visual Studio, kaynak denetimi VSPackage'ları ile kaynak denetimi eklentileri arasında el ile geçişe ve otomatik çözüm tabanlı anahtarlamaya olanak sağlar.

## <a name="source-control-integration"></a>Kaynak Denetimi Tümleştirmesi
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] iki tür kaynak denetimi tümleştirme seçeneklerini destekler. Tüm sürümlerinde, eklentiyi kaynak denetimi kullanıcı arabirimini (UI) kullanırken temel kaynak denetimi işlevselliği sağlayan Kaynak Denetimi Eklentisi API'sini (daha önce MSSCCI API'si olarak da adlandırılır) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Visual Studio temel alarak tümleştirebilirsiniz. Diğer taraftan kaynak denetimi VSPackage, kaynak denetim modelinde yüksek düzeyde gelişmişlik ve otonomi talep etmek için kaynak denetimi tümleştirmesi için uygun yeni, derin bir [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] tümleştirme yolu sağlar.

 ![Kaynak Denetimine Genel Bakış](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>Kaynak Denetimi Eklentisi
 Tüm sürümler Visual Studio kaynak denetimi eklenti API'si belirtimi sürüm 1.2'yi tümleştirme yolu olarak destekler. Kaynak denetimi eklentisi uygulayan, Kaynak Denetimi Eklentisi Oluşturma konusunda açıklandığı gibi kaynak denetimi tümleştirmesi ve kaydı için Kaynak Denetimi Eklentisi API'si işlevlerini uygulayan bir DLL [yazar.](../../extensibility/internals/creating-a-source-control-plug-in.md) Bu yaklaşımda Tümleşik Geliştirme Ortamı (IDE) iade, iade, araç/seçenek özellik sayfaları, araç çubukları ve kaynak denetimi özellikleri gibi iletişim kutuları için kullanıcı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arabirimini kullanır. Kaynak Denetimi Eklentisi API'sine katı bir şekilde bağlılık, Visual Studio ve kullanıcı için sorun olmayan bir deneyimle kolay bir tümleştirme sağlar. Bu, kaynak denetimi eklentisinin API'de ayrıntılı olarak yer alan işlevlerin ve geri çağırmaların çoğunu uygulaması gerektiğini gösterir.

 Kaynak Denetimi Eklentisi API'sini kullanarak bir kaynak denetimi eklentisi uygulamak için şu adımları izleyin:

1. Kaynak Denetimi Eklentileri'ne belirtilen işlevleri [uygulayan bir](../../extensibility/source-control-plug-ins.md)DLL oluşturun.

2. Uygun kayıt defteri girdilerini yaparak DLL'i kaydetme [(Nasıl: Kaynak Denetimi Eklentisi Yükleme konusunda açıklanmıştır).](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

3. Kaynak Denetim Bağdaştırıcısı Paketi (kaynak denetimi eklentileri aracılığıyla kaynak denetimi işlevselliğini Visual Studio bileşeni) istendiğinde bir yardımcı kullanıcı arabirimi oluşturun ve görüntü oluşturun

   Bir kaynak denetimi komutuna yanıt olarak, Visual Studio IDE temel işlemler için standart bir kullanıcı arabirimi sunar ve ardından Kaynak Denetimi Eklentisi API'sinde tanımlanan işlevler aracılığıyla bilgileri kaynak denetimi eklentisine iletir. Gelişmiş seçenekler için kaynak denetim eklentisi, kaynak denetimli projeye göz atma gibi kendi kullanıcı arabirimini sunmak için çağrılmalıdır. Bu, kaynak denetimiyle ilgilenmek için kullanıcıya iki farklı kullanıcı arabirimi stili sunabilirsiniz: Visual Studio kullanıcı arabirimi ve kaynak denetimi eklentisinin sunduğu kullanıcı arabirimi. Bu, en çok gelişmiş kaynak denetimi işlemleriyle fark edilebilir.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Kaynak Denetimi Eklentisi Uygulamanın Dezavantajları

- Gelişmiş özellikler için kullanıcı iki farklı arabirim stili görebilir ve bu da olası karışıklıklara yol açabilir.

- Kaynak denetimi eklentisi, Kaynak Denetimi Eklentisi API'si tarafından kapsan kaynak denetim modeliyle sınırlandı.

- Kaynak Denetimi Eklentisi API'si bazı kaynak denetimi senaryoları için fazla kısıtlayıcı olabilir.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Kaynak Denetimi Eklentisi Uygulamanın Avantajları

- Visual Studio tüm temel kaynak denetimi işlemleri için tüm kullanıcı arabirimini sağlar, böylece kaynak denetimi eklentisinin karmaşık olabilecek kullanıcı arabirimini uygulamasına gerek olmaz.

- Katı API nedeniyle, kaynak denetimi eklentisi daha kapsamlı işlevsellik sağlamak için dış kaynak denetimi programlarıyla etkileşime hazır olabilir; Visual Studio denetimi işlevselliğinin ne kadar başarılı olduğu çok önemli değildir, yalnızca Kaynak Denetimi Eklentisi API'sini temel alan bir şekilde gerçektir.

- Kaynak denetimi eklentisinin uygulanması, vsPackage kaynak denetiminden daha kolaydır.

## <a name="source-control-vspackage"></a>Kaynak Denetimi VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], kaynak denetimi işlevselliğinin tam Visual Studio ve sağlanan kaynak denetimi kullanıcı arabiriminin tam Visual Studio ile Visual Studio tümleştirmeye olanak sağlar. VsPackage kaynak denetimi, Visual Studio ve kaynak denetimi işlevselliği sağlar. Çeşitli kaynak denetimi VSPackage'ları Visual Studio, ancak herhangi bir anda yalnızca biri etkin olabilir. Bir kaynak denetimi VSPackage, etkin olduğu sırada kaynak denetimi işlevselliği ve Visual Studio tam denetime sahiptir. Sistemde kayıtlı olan diğer tüm kaynak denetimi VSPackage'ları etkin değildir ve hiçbir kullanıcı arabirimi görüntülemez.

 VSPackage kaynak denetimi uygulamak için "hepsi veya hiçbir şey" stratejisi gerekir. VSPackage kaynak denetimi oluşturucusu, kaynak denetimi işlevselliğinin tamamını kapsayacak şekilde bir dizi kaynak denetimi arabirimi ve yeni kullanıcı arabirimi öğesini (iletişim kutuları, menüler ve araç çubukları) uygulamak için önemli miktarda çaba göstermalıdır. Daha [fazla ayrıntı için bkz. Kaynak Denetimi VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md) Oluşturma.

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Kaynak Denetimi VSPackage Uygulamanın Dezavantajları

- VSPackage' ın bir dizi karmaşık arabirimini uygulamalı ve bu arabirimle başarıyla Visual Studio.

- VSPackage, kaynak denetimi için gereken tüm kullanıcı arabirimini sağlar; Visual Studio bu alanda hiçbir yardım sağlamaz.

- Kaynak denetimi VSPackage, Visual Studio tek başına programlarla çalışamaz ve bu nedenle işlevsellik, kaynak denetim programının dış bir sürümüyle kolayca paylaşılamaz.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Kaynak Denetimi VSPackage Uygulamanın Avantajları

- VSPackage kaynak denetimi kullanıcı arabirimi ve işlevselliği üzerinde tam denetime sahip olduğundan, kullanıcıya kaynak denetimi için sorunsuz bir arabirim sunulmaktadır.

- VSPackage belirli bir kaynak denetim modeliyle sınırlı değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi](../../extensibility/internals/source-control.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Kaynak Denetimi VSPackage’ı Oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Kaynak Denetimindeki Yenilikler](../../extensibility/internals/what-s-new-in-source-control.md)
