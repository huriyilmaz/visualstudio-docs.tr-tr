---
title: Paylaşılan ve Sürümlü VSPackages Arasında Seçim | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21fefb776fceeeef4db6997a5bd12a8b987af7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739879"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Paylaşılan ve sürümlenmiş VSPackages arasında seçim yapın
Visual Studio'nun farklı sürümleri aynı bilgisayarda bir arada bulunabilir. VSPackages [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sürümleri herhangi bir karışımını destekleyebilir.

 VsPackages'ın yan yana kurulumlarını iki stratejiden, paylaşılan stratejiden veya sürümlenmiş stratejiden herhangi biri aracılığıyla etkinleştirebilirsiniz. Her ikisi de .NET [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Framework'ün birden çok sürümü ve ilişkili sürümlerinin varlığını barındırır.

 Paylaşılan stratejide, bir VSPackage birden fazla sürümünde kullanılmak üzere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]kaydedilir. Sürümlenmiş stratejide, desteklediğiniz her sürüm [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] için birden çok VSPackage DL'si yüklenir.

## <a name="shared-vspackages"></a>Paylaşılan VSPackages
 Aynı VSPackage'ı birden fazla sürümde kullandığınızda paylaşılan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]bir VSPackage kullanmak uygundur. Paylaşılan bir VSPackage uygulamak için aşağıdaki adımları gerçekleştirmeniz gerekir:

- VSPackage'ınızı birden fazla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]sürümüyle uyumlu hale getirin. Bunu yapmanın iki yolu vardır:

  - VSPackage'ınızı yalnızca desteklediğiniz en eski sürümün [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] özelliklerini kullanarak sınırlandırın.

  - VSPackage'ınızı çalıştığı sürüme [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uyum sağlayacak şekilde programla. Daha sonra, yeni hizmetler için sorgular başarısız olursa, VSPackage eski sürümlerinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]desteklenen diğer hizmetler sunabilir.

- VSPackage'ınızı uygun şekilde kaydedin. Daha fazla bilgi için [VSPackage kaydı](../extensibility/internals/vspackage-registration.md) ve Yönetilen [VSPackage kaydına](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)bakın.

- Dosya uzantılarını uygun şekilde kaydedin. Daha fazla bilgi için, [yan yana dağıtımlar için dosya adı uzantılarını kaydetme'ye](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)bakın.

- UYGUN sürümleri için VSPackage dağıtır bir yükleyici [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]oluşturun. Daha fazla bilgi için Windows Installer ve [Bileşen yönetimi](../extensibility/internals/component-management.md) [ile VSPackages Yükleme'ye](../extensibility/internals/installing-vspackages-with-windows-installer.md) bakın.

- Kayıt çakıştığı sorununu ele alın. Daha fazla bilgi için [VSPackage kaydına](../extensibility/internals/vspackage-registration.md)bakın.

- Paylaşılan ve sürümlenmiş dosyaların, birden çok sürümün güvenli bir şekilde yüklenmesine ve kaldırılmasına izin vermek için başvuru saymaya uygun olduğundan emin olun. Daha fazla bilgi için [Bileşen yönetimine](../extensibility/internals/component-management.md)bakın.

## <a name="versioned-vspackages"></a>Versiyonlu VSPackages
 Sürümlenmiş VSPackage stratejisi altında, desteklediğiniz her sürüm [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] için bir VSPackage oluşturursunuz. Bunu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]yapmak, sonraki sürümleritarafından sağlanan hizmetlerden yararlanmayı beklediğiniz zaman uygundur, çünkü her VSPackage diğerlerini etkilemeden gelişebilir. Bununla birlikte, tek bir kod tabanından veya birden çok bağımsız kod tabanından birden çok ikili oluşturma sürümünde strateji, paylaşılan stratejiden daha fazla ilk geliştirme gerektirebilir. Ayrıca, her sürüm için ayrı bir kurulum veya yüklü olan sürümlerini algılayan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve VSPackage'ınızın desteklediği tek bir kurulum oluşturmanız gerektiğinden ek kurulum çalışması gerekebilir.

## <a name="binary-compatibility"></a>İkili uyumluluk
 Genellikle ikili uyumluluk, Visual Studio'nun önceki sürümleriyle geliştirilen yerel kodLU VSPackages'in Visual Studio'nun sonraki sürümlerinde çalışmasını sağlar. Ancak, üç önemli istisna vardır:

- VSPackage'ınız ortak dil çalışma zamanının belirli bir sürümüne dayanıyorsa, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hangi sürümünde çalıştığını belirlemelidir.

- VSPackage, başka bir VSPackage veya başka bir ürünün belirli bir özelliğine bağımlı olabilir. Sonuç olarak, VSPackage yalnızca bağımlılık memnun olduğunda çalıştırabilirsiniz.

- VSPackage, bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hizmet paketindeki güvenlik düzeltmesi veya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]daha sonraki bir sürümden etkilenebilir. Bu gibi durumlarda, güvenlik düzeltmesi uygulandıktan [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sonra sürümlerinde çalıştırılamayabilir önceki bir sürümü ile geliştirilen bir VSPackage. Ancak, paketinizi sonraki sürümle yeniden oluşturabilirsiniz ve önceki sürümlerde de çalıştırabilirsiniz.

  Yönetilen VSPackages bir sürümü kullanılarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inşa [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] edilmelidir ve bu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]hedef sürümü maç .

  VSPackage ikili ikili için ikili uyumluluk için planlama ek olarak, ayrıca çözüm ve proje dosya biçimleri düşünmelisiniz. VSPackage'ınız yeni bir proje türü oluşturuyorsa, yalnızca bir sürümde mi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]yoksa birden çok sürümde mi çalıştırılamayacağına karar vermelisiniz. Daha fazla bilgi için [bkz.](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer ile VSPackages yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Bileşen yönetimi](../extensibility/internals/component-management.md)
