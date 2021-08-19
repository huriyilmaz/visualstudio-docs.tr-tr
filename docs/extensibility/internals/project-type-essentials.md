---
title: Project Type Essentials | Microsoft Docs
description: Proje türü oluşturmanın ne zaman gerektiğini ve proje alt türlerini kullanarak mevcut bir proje türünü ne zaman genişletip genişleteceniz hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 251b9f9b17e5e20e7a2d039a77155bd2be457388
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117845"
---
# <a name="project-type-essentials"></a>Proje Türü Temel Bileşenleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , veya gibi diller için çeşitli proje türleri [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] içerir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayrıca kendi proje türlerinizi oluşturmanıza da olanak sağlar.

 'a yalnızca özel komutlar, düzenleyiciler veya araç pencereleri eklemek için yeni bir proje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] türü oluşturmadan bunu yapabilirsiniz. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Komutlar, Menüler ve Araç Çubukları](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Düzenleyici ve Dil Hizmeti Uzantıları](../../extensibility/editor-and-language-service-extensions.md)

- [Araç Pencerelerini Genişletme ve Özelleştirme](../../extensibility/extending-and-customizing-tool-windows.md)

  Benzer şekilde, sağlanan ve proje türlerinin davranışını özelleştirmek [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] için proje alt türlerini kullanarak bunu da [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] yapabiliriz. Daha fazla bilgi için [bkz. Project Alt Türleri.](../../extensibility/internals/project-subtypes.md)

  Aşağıdakilerden birini veya daha fazlasını desteklemek için ve dışında bir dili temel alan projeler için yeni bir proje [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] türü oluşturmanız gerekir:

- Oluşturma

- Dağıtım

- Birden çok yapılandırma

- Kaynak denetimi

- Hata Ayıklama

- Project öğeleri Çözüm Gezgini

- Açık **Project** veya **Yeni Project** iletişim kutuları

- Project iç içe yerleştirme

- Proje türlerinin özellikleri hakkında daha fazla bilgi için aşağıdakilere bakın:

- Project, bir VSPackage içinde beklediğiniz arabirimleri uygulayan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nesnelerdir. Bir proje türü geliştirmek için C# kullanıyorsanız, Yönetilen Paket Çerçevesi proje sınıfları sizin için gerekli arabirimleri uygulayan ve bu uygulamanın devralınmalarını sağlar. Daha fazla bilgi için, [bkz. Using the Managed Package Framework to Implement a Project Type (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- C++ geliştiricileri için, HierUtil kitaplığında sınıflar benzer şekilde çalışır. Daha fazla bilgi için, [bkz. Not in Build: Using HierUtil7 Project Classes to Implement a Project Type (C++)](/previous-versions/bb166212(v=vs.100)).

- Project türleri, bir derlemede veya derlemede bir derlemede yer alan tipik kaynak .exe .dll destekleyebilirsiniz. Örneğin, veritabanı projeleri diskte depolanan betik ve sorgu dosyalarına başvurular içerir ve betikleri ve sorguları bir veritabanında yürütmek için Çözüm Gezgini'a komutlar ekler, ancak projeler derleme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] davranışını desteklemez.  Daha fazla bilgi için [bkz. Öğeleri Açma Project Kaydetme.](../../extensibility/internals/opening-and-saving-project-items.md)

- Proje türünün dosyaları kullanmak zorunda değildir. Örneğin, bir proje türü tüm verilerini bir veritabanında depolar. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje türlerine, projeler ve proje öğeleri için verilerin nasıl kalıcı olduğu üzerinde tam denetim sağlar. Daha fazla bilgi için [bkz. Project Tür Tasarımı Kararları.](../../extensibility/internals/project-type-design-decisions.md)

- Project türleri, bu proje türünü temel alan bir proje açması veya oluşturması isnilen her durumda proje türünün bir örneğini oluşturan bir nesne olan proje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fabrikasını sağlasalar. Daha fazla bilgi için, [bkz. Creating Project By Using Project Instances](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Project türleri projeler ve proje öğeleri için şablonlar sağlamak gerekir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , kullanıcılar yeni projeler oluşturdukları ve mevcut projelere yeni öğeler ekley maddelerini kullandığında şablonları kullanır. Daha fazla bilgi için [bkz. Project ve Project Şablonları Ekleme.](../../extensibility/internals/adding-project-and-project-item-templates.md)

- Project, Hata Ayıklama ve Yayın gibi birden çok yapılandırmayı destekleyebildi. Kullanıcılar, sizin temin ettiyniz özellik sayfalarını kullanarak projenin farklı yapılandırmalarını değiştirebilir. Daha fazla bilgi için [bkz. Yapılandırma Seçeneklerini Yönetme.](../../extensibility/internals/managing-configuration-options.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Türlerini Dağıtma](../../extensibility/internals/deploying-project-types.md)