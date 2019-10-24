---
title: Proje türü temelleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 435d3ca0e35911754cac1e37abb276939109a0b3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725404"
---
# <a name="project-type-essentials"></a>Proje Türü Temel Bileşenleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] veya [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] gibi dillerin çeşitli proje türlerini içerir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ayrıca kendi proje türlerinizi oluşturmanızı sağlar.

 Yalnızca [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için özel komutlar, düzenleyiciler veya araç pencereleri eklemek istiyorsanız, bunu yeni bir proje türü oluşturmadan yapabilirsiniz. Daha fazla bilgi için aşağıdaki konulara bakın:

- [Komutlar, Menüler ve Araç Çubukları](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Düzenleyici ve Dil Hizmeti Uzantıları](../../extensibility/editor-and-language-service-extensions.md)

- [Araç Pencerelerini Genişletme ve Özelleştirme](../../extensibility/extending-and-customizing-tool-windows.md)

  Benzer şekilde, sağlanan [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proje türlerinin davranışını özelleştirmek istiyorsanız, bunu proje alt türlerini kullanarak yapabilirsiniz. Daha fazla bilgi için bkz. [Proje alt türleri](../../extensibility/internals/project-subtypes.md).

  Aşağıdakilerden birini veya birkaçını desteklemek istiyorsanız, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] dışındaki bir dili temel alan projeler için yeni bir proje türü oluşturmanız gerekir:

- Yapı

- Dağıtım

- Birden çok yapılandırma

- Kaynak denetimi

- Hata Ayıklama

- Çözüm Gezgini proje öğeleri

- **Açık proje** veya **Yeni proje** iletişim kutuları

- İçe proje iç içe

- Proje türlerinin özellikleri hakkında daha fazla bilgi için aşağıdakilere bakın:

- Proje türleri, beklediği [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arabirim kümesini uygulayan VSPackage içindeki nesnelerdir. Bir proje türü geliştirmek C# için kullanıyorsanız, yönetilen paket çerçevesi proje sınıfları sizin için gerekli arabirimleri uygular ve bu uygulamayı devralmasını sağlar. Daha fazla bilgi için bkz. [bir proje türü (C#) uygulamak Için yönetilen paket çerçevesini kullanma](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- Geliştiriciler C++ Için, HierUtil kitaplığındaki sınıflar benzer bir şekilde çalışır. Daha fazla bilgi için bkz. [derlemede değil: bir proje türü (C++) uygulamak Için HierUtil7 proje sınıflarını kullanma](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Proje türleri, bir. exe veya. dll derlemesine oluşturan tipik kaynak kodu dosyalarından farklı verileri destekleyebilir. Örneğin, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] veritabanı projeleri, diske depolanan betiklerin ve sorgu dosyalarının başvurularını içerir ve bir veritabanına karşı betikleri ve sorguları yürütmek için **Çözüm Gezgini** komutlar ekler, ancak projeler derleme davranışını desteklemez. Daha fazla bilgi için bkz. [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md).

- Proje türü, dosyaları kullanmak zorunda değildir. Örneğin, bir proje türü tüm verilerini bir veritabanında saklayabilir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeler ve proje öğeleri için verileri nasıl kalıcı hale getirebilecekleri üzerinde proje türlerine tamamen denetim sağlar. Daha fazla bilgi için bkz. [Proje türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md).

- Proje türleri bir proje *fabrikası*sağlamalıdır ve bu proje türünü temel alan bir proje açmak ya da oluşturmak için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] her seferinde proje türünün bir örneğini oluşturan bir nesne olmalıdır. Daha fazla bilgi için bkz. [Proje fabrikalarını kullanarak proje örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Proje türleri, projeler ve proje öğeleri için şablon sağlamalıdır. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], kullanıcılar yeni projeler oluştururken ve varolan projelere yeni öğeler eklerken şablonları kullanır. Daha fazla bilgi için bkz. [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Proje türleri, hata ayıklama ve yayın gibi birden fazla yapılandırmayı destekleyebilir. Kullanıcılar, sağladığınız özellik sayfalarını kullanarak bir projenin farklı yapılandırmasını değiştirebilir. Daha fazla bilgi için bkz. [yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Türlerini Dağıtma](../../extensibility/internals/deploying-project-types.md)