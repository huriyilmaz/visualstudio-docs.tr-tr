---
title: Proje türü temelleri | Microsoft Docs
description: Proje türünü ne zaman oluşturmanız gerektiğini ve proje alt türlerini kullanarak var olan bir proje türünü genişletebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 86ed1c1098fe13cd19ce686782e18b190f455f8c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064299"
---
# <a name="project-type-essentials"></a>Proje Türü Temel Bileşenleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , veya gibi diller için birçok proje türü [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] içerir [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ayrıca kendi proje türlerinizi oluşturmanıza imkan tanır.

 Yalnızca öğesine özel komutlar, düzenleyiciler veya araç pencereleri eklemek istiyorsanız [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , bunu yeni bir proje türü oluşturmadan yapabilirsiniz. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Komutlar, Menüler ve Araç Çubukları](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Düzenleyici ve Dil Hizmeti Uzantıları](../../extensibility/editor-and-language-service-extensions.md)

- [Araç Pencerelerini Genişletme ve Özelleştirme](../../extensibility/extending-and-customizing-tool-windows.md)

  Benzer şekilde, sağlanan ve proje türlerinin davranışını özelleştirmek istiyorsanız, bunu [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Proje alt türlerini kullanarak yapabilirsiniz. Daha fazla bilgi için bkz. [Proje alt türleri](../../extensibility/internals/project-subtypes.md).

  [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Aşağıdakilerden birini veya birkaçını desteklemek istiyorsanız, dışındaki bir dili temel alan projeler için yeni bir proje türü oluşturmanız gerekir:

- Derleme

- Dağıtım

- Birden çok yapılandırma

- Kaynak denetimi

- Hata Ayıklama

- Çözüm Gezgini proje öğeleri

- **Açık proje** veya **Yeni proje** iletişim kutuları

- İçe proje iç içe

- Proje türlerinin özellikleri hakkında daha fazla bilgi için aşağıdakilere bakın:

- Proje türleri, beklenen arabirim kümesini uygulayan bir VSPackage nesneleridir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bir proje türü geliştirmek Için C# kullanıyorsanız, yönetilen paket çerçevesi proje sınıfları sizin için gerekli arabirimleri uygular ve bu uygulamayı devralmasını sağlar. Daha fazla bilgi için bkz. [bir proje türü uygulamak Için yönetilen paket çerçevesini kullanma (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- C++ geliştiricileri için, HierUtil kitaplığındaki sınıflar benzer bir şekilde çalışır. Daha fazla bilgi için bkz. [derlemede değil: bir proje türü uygulamak Için HierUtil7 proje sınıflarını kullanma (C++)](/previous-versions/bb166212(v=vs.100)).

- Proje türleri, bir. exe veya. dll derlemesine oluşturan tipik kaynak kodu dosyalarından farklı verileri destekleyebilir. Örneğin, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] veritabanı projeleri disk üzerinde depolanan betik ve sorgu dosyalarının başvurularını içerir ve bir veritabanına karşı betikleri ve sorguları yürütmek için **Çözüm Gezgini** komutlar ekler, ancak projeler derleme davranışını desteklemez. Daha fazla bilgi için bkz. [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md).

- Proje türü, dosyaları kullanmak zorunda değildir. Örneğin, bir proje türü tüm verilerini bir veritabanında saklayabilir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje türlerine, projelere ve proje öğelerine yönelik verileri nasıl kalıcı hale getirebileceği üzerinde tüm denetim sağlar. Daha fazla bilgi için bkz. [Proje türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md).

- Proje türleri bir proje *fabrikası* sağlamalıdır ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Bu proje türünü temel alan bir proje açmak veya oluşturmak için her zaman proje türünün bir örneğini oluşturan bir nesne olmalıdır. Daha fazla bilgi için bkz. [Proje fabrikalarını kullanarak proje örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Proje türleri, projeler ve proje öğeleri için şablon sağlamalıdır. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kullanıcılar yeni projeler oluştururken ve varolan projelere yeni öğeler eklerken şablonları kullanır. Daha fazla bilgi için bkz. [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Proje türleri, hata ayıklama ve yayın gibi birden fazla yapılandırmayı destekleyebilir. Kullanıcılar, sağladığınız özellik sayfalarını kullanarak bir projenin farklı yapılandırmasını değiştirebilir. Daha fazla bilgi için bkz. [yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Türlerini Dağıtma](../../extensibility/internals/deploying-project-types.md)