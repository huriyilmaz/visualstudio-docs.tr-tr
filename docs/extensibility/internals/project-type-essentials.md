---
title: Proje Türü Temelleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b44da532207668d9526aec0ccdcab027b94184e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706377"
---
# <a name="project-type-essentials"></a>Proje Türü Temel Bileşenleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)][!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] gibi diller için çeşitli proje [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]türleri içerir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ayrıca kendi proje türlerinizi oluşturmanıza olanak tanır.

 Sadece özel komutlar, editörler veya araç pencereleri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]eklemek istiyorsanız, bunu yeni bir proje türü oluşturmadan yapabilirsiniz. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Komutlar, Menüler ve Araç Çubukları](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Düzenleyici ve Dil Hizmeti Uzantıları](../../extensibility/editor-and-language-service-extensions.md)

- [Araç Pencerelerini Genişletme ve Özelleştirme](../../extensibility/extending-and-customizing-tool-windows.md)

  Aynı şekilde, sağlanan [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proje türlerinin davranışını özelleştirmek istiyorsanız, bunu proje alt türlerini kullanarak yapabilirsiniz. Daha fazla bilgi için [Bkz. Proje Alt Türleri.](../../extensibility/internals/project-subtypes.md)

  Aşağıdakilerden birini veya daha fazlasını desteklemek [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] istiyorsanız, başka [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] bir dile dayanan ve aşağıdakilerden birini veya daha fazlasını desteklemek istiyorsanız, projeler için yeni bir proje türü oluşturmanız gerekir:

- Yapı

- Dağıtım

- Birden çok yapılandırma

- Kaynak denetimi

- Hata Ayıklama

- Çözüm Gezgini'ndeki proje öğeleri

- **Projeyi Aç** veya **Yeni Proje** iletişim kutuları

- Proje iç içe

- Proje türlerinin yetenekleri hakkında daha fazla bilgi için aşağıdakilere bakın:

- Proje türleri, beklediği arabirimler kümesini uygulayan VSPackage'daki nesnelerdir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Bir proje türü geliştirmek için C# kullanıyorsanız, Yönetilen Paket Çerçevesi proje sınıfları sizin için gerekli arabirimleri uygular ve bu uygulamayı devralmanıza izin verilir. Daha fazla bilgi için, [Proje Türü (C#) uygulamak için Yönetilen Paket Çerçevesini Kullanma'ya](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)bakın.

- C++ geliştiricileri için HierUtil kitaplığındaki sınıflar benzer şekilde çalışır. Daha fazla bilgi için [yapıda değil: Proje Türünü (C++) Uygulamak için HierUtil7 Proje Sınıflarını Kullanma.](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)

- Proje türleri, .exe veya .dll derlemesi oluşturan tipik kaynak kodu dosyaları dışındaki verileri destekleyebilir. Örneğin, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] veritabanı projeleri diskte depolanan komut dosyası ve sorgu dosyalarına başvurular içerir ve komut dosyalarını ve sorguları veritabanına karşı yürütmek için **Solution Explorer'a** komutlar ekler, ancak projeler yapı davranışını desteklemez. Daha fazla bilgi için [bkz.](../../extensibility/internals/opening-and-saving-project-items.md)

- Proje türü dosyaları hiç kullanmak zorunda değildir. Örneğin, bir proje türü tüm verilerini bir veritabanında depolayabilir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]proje türlerine, projeler ve proje öğeleri için verileri nasıl devam ettikleri üzerinde tam denetim sağlar. Daha fazla bilgi için [Proje Türü Tasarım Kararları'na](../../extensibility/internals/project-type-design-decisions.md)bakın.

- Proje türlerinin, bu *proje*türünü temel alan bir projeyi açması [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] veya oluşturması söylendiğinde proje türünün bir örneğini oluşturan bir nesne olan bir proje fabrikası sağlaması gerekir. Daha fazla bilgi için bkz: [Proje Fabrikalarını Kullanarak Proje Örnekleri Oluşturma.](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

- Proje türleri, projeler ve proje öğeleri için şablonlar sağlamalıdır. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kullanıcılar yeni projeler oluşturduğunda ve varolan projelere yeni öğeler eklediğinde şablonları kullanır. Daha fazla bilgi için [bkz.](../../extensibility/internals/adding-project-and-project-item-templates.md)

- Proje türleri Hata Ayıklama ve Sürüm gibi birden çok yapılandırmayı destekleyebilir. Kullanıcılar, sağladığınız özellik sayfalarını kullanarak projenin farklı yapılandırmalarını değiştirebilir. Daha fazla bilgi için yapılandırma [seçeneklerini yönetme'ye](../../extensibility/internals/managing-configuration-options.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Türlerini Dağıtma](../../extensibility/internals/deploying-project-types.md)
