---
title: Project modelinin öğeleri | Microsoft Docs
description: proje modelinin öğeleri ve Visual Studio içindeki tüm projelere ait arabirimlerin ve uygulamaların temel yapıyı nasıl paylaştığından ilgili bilgi edinin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725082"
---
# <a name="elements-of-a-project-model"></a>Proje modelinin öğeleri
Temel yapıyı paylaşan tüm projelerin arabirimleri ve uygulamaları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] : proje türü için proje modeli. Geliştirmekte olduğunuz VSPackage olan proje modelinizde, tasarım kararlarınızla uyumlu olan ve IDE tarafından sunulan genel işlevlerle birlikte çalışan nesneler oluşturursunuz. Bir proje öğesinin nasıl kalıcı olduğunu denetlemenize karşın, örneğin, bir dosyanın kalıcı olması gerektiğini kontrol edersiniz. Bir Kullanıcı, odağı açık bir proje öğesine yerleştiriyor ve menü çubuğundaki **Dosya** menüsünde **Kaydet** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ' i SEÇTIĞINDE, proje türü kodunuz IDE 'den komutu ele almalıdır, dosyayı kalıcı hale getirin ve dosyanın artık değiştirilmediğini daha sonra geri bildirim gönderir.

 VSPackage, IDE arabirimlerine erişim sağlayan hizmetler aracılığıyla IDE ile etkileşime girer. Örneğin, belirli hizmetler aracılığıyla komutları izleyip yönlendirebilir ve projede yapılan seçimlere yönelik bağlam bilgilerini sağlarsınız. VSPackage için gereken tüm Global IDE işlevleri hizmetler tarafından sağlanmaktadır. Hizmetler hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmet alma](../../extensibility/how-to-get-a-service.md).

 Diğer uygulama konuları:

- Tek bir proje modelinde birden fazla proje türü bulunabilir.

- Project türleri ve ilgili proje fabrikaları, guıd 'lerle bağımsız olarak kaydedilir.

- Kullanıcı Kullanıcı arabirimi aracılığıyla yeni bir proje oluşturduğunda, her projenin yeni proje dosyasını başlatması için bir şablon dosyası veya Sihirbazı olması gerekir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Örneğin, şablonlar, son olarak [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] . vcproj dosyaları olmaya başlatırlar.

  Aşağıdaki çizimde, tipik bir proje uygulamasını oluşturan birincil arabirimler, hizmetler ve nesneler gösterilmektedir. `HierUtil7`Temel nesneleri ve diğer programlama ortak nesnelerini oluşturmak için uygulama yardımcısını kullanabilirsiniz. Uygulama Yardımcısı hakkında daha fazla bilgi için `HierUtil7` bkz. [bir proje türü uygulamak için HierUtil7 proje sınıflarını kullanma (C++)](/previous-versions/bb166212(v=vs.100)).

  ![Visual Studio proje modeli grafik](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") Project modeli

  önceki diyagramda listelenen arabirimler ve hizmetler ve diyagramda bulunmayan diğer isteğe bağlı arabirimler hakkında daha fazla bilgi için bkz. [Project model çekirdek bileşenleri](../../extensibility/internals/project-model-core-components.md).

  Projeler komutları destekleyebilir ve bu nedenle komut <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> yönlendirme GUID 'leri aracılığıyla komut yönlendirmesine katılmak için arabirimi uygulamalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Denetim listesi: yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje türü uygulamak için HierUtil7 proje sınıflarını kullanma (C++)](/previous-versions/bb166212(v=vs.100))
- [Project modeli çekirdek bileşenleri](../../extensibility/internals/project-model-core-components.md)
- [Proje fabrikalarını kullanarak proje örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Nasıl yapılır: hizmet alma](../../extensibility/how-to-get-a-service.md)
- [Proje türleri oluştur](../../extensibility/internals/creating-project-types.md)