---
title: Project Model | Microsoft Docs
description: Proje modelinin öğeleri ve Visual Studio'daki tüm projelerin arabirimlerinin ve Visual Studio temel bir yapıyı nasıl paylaştığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a3e967466bef5feabaa4e6760dfc73c2927e7b35
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110585"
---
# <a name="elements-of-a-project-model"></a>Proje modelinin öğeleri
'daki tüm projelerin arabirimleri ve uygulamaları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] temel bir yapıyı paylaşır: proje türünüz için proje modeli. Geliştirdiğiniz VSPackage olan proje modelinize, tasarım kararlarınızı uygun nesneler oluşturur ve IDE tarafından sağlanan genel işlevlerle birlikte çalışır. Örneğin, bir proje öğesinin nasıl kalıcı olduğunu denetlemenizle birlikte, bir dosyanın kalıcı olması gerektiğinin bildirimini denetlemezsiniz. Kullanıcı odağı açık bir proje öğesine yer  değiştirse  ve menü çubuğundaki Dosya menüsünde Kaydet'i seçtiklerinde, proje türü kodunuz IDE'den komutu kesmeli, dosyayı kalıcı olmalı ve dosyanın artık değişmediğini IDE'ye geri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] göndermeli.

 VSPackage'nız, IDE arabirimlerine erişim sağlayan hizmetler aracılığıyla IDE ile etkileşime geçiyor. Örneğin, belirli hizmetler aracılığıyla komutları izlep yönlendirin ve projede yapılan seçimler için bağlam bilgileri sağlarsınız. VSPackage'nız için gereken tüm genel IDE işlevleri hizmetler tarafından sağlanır. Hizmetler hakkında daha fazla bilgi için [bkz. Nasıl: Hizmet al.](../../extensibility/how-to-get-a-service.md)

 Diğer uygulama konuları:

- Tek bir proje modeli birden fazla proje türü içerebilir.

- Project türler ve proje fabrikaları GUID'lerle bağımsız olarak kaydedilir.

- Kullanıcı kullanıcı arabirimi aracılığıyla yeni bir proje oluşturduğunda yeni proje dosyasını başlatmak için her projenin bir şablon dosyası veya sihirbazı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] olması gerekir. Örneğin, şablonlar [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] sonunda .vcproj dosyaları haline gelecek dosyaları başlatıyor.

  Aşağıdaki çizimde, tipik bir proje uygulamasını oluşturan birincil arabirimler, hizmetler ve nesneler gösterilmiştir. Temel alınan nesneleri ve diğer programlama ortaklarını oluşturmak için uygulama `HierUtil7` yardımcısını kullanabilirsiniz. Uygulama yardımcısı hakkında daha fazla bilgi için bkz. Proje türünü uygulamak için `HierUtil7` [HierUtil7 proje sınıflarını kullanma (C++)](/previous-versions/bb166212(v=vs.100)).

  ![Visual Studio modeli grafik Project](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") modeli

  Önceki diyagramda listelenen arabirimler ve hizmetler ve diyagrama dahil edilen diğer isteğe bağlı arabirimler hakkında daha fazla bilgi için [bkz. Project temel bileşenleri.](../../extensibility/internals/project-model-core-components.md)

  Projeler komutları destekleyeyene sahip olabilir ve bu nedenle komut bağlamı GUID'leri aracılığıyla komut <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> yönlendirmeye katılmak için arabirimini uygulaması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Denetim listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje türü uygulamak için HierUtil7 proje sınıflarını kullanma (C++)](/previous-versions/bb166212(v=vs.100))
- [Project modeli temel bileşenleri](../../extensibility/internals/project-model-core-components.md)
- [Proje fabrikalarını kullanarak proje örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Nasıl: Hizmet al](../../extensibility/how-to-get-a-service.md)
- [Proje türleri oluşturma](../../extensibility/internals/creating-project-types.md)