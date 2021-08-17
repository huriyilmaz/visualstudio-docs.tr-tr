---
title: Paylaşılan ve Sürüme Sahip VSPackage'lar Arasında Seçim | Microsoft Docs
description: Paylaşılan veya sürüme sahip stratejiler aracılığıyla VSPackage'ların birden çok sürümü ve Visual Studio yan yana yüklemeleri hakkında .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 34bd5db7f02b69c5f2f3e9b017f7cccbabbf175cfe70ba70af0efb835f7ecc4f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434951"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Paylaşılan ve sürüme sahip VSPackage'lar arasında seçim
Farklı Visual Studio aynı bilgisayarda bir arada var olabilir. VSPackage'lar sürümlerin herhangi bir karışımını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] destekler.

 VSPackage'ların yan yana yüklemelerini iki stratejiden birini (paylaşılan strateji veya sürümli strateji) etkinleştirebilirsiniz. Her ikisi de uygulamanın birden çok [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sürümünün ve ilişkili sürümlerinin varlığını .NET Framework.

 Paylaşılan stratejide, bir VSPackage birden çok sürümlerinde kullanım için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kaydedilir. Sürüme yüklenmiş stratejide, destekleyenin her sürümü için bir tane olmak için birden çok VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] DLL'i yüklenir.

## <a name="shared-vspackages"></a>Paylaşılan VSPackage'lar
 Birden çok sürümde aynı VSPackage'ı kullanırken paylaşılan VSPackage kullanmak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uygundur. Paylaşılan bir VSPackage uygulamak için aşağıdaki adımları izleyebilirsiniz:

- VSPackage'nızı birden çok sürümüyle uyumlu hale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] geldi. Bunu yapmak için iki yol vardır:

  - VSPackage'ını yalnızca destekleyenin en eski sürümünün [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] özelliklerini kullanarak sınırla.

  - VSPackage'nızı içinde çalıştırıldık [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sürümüne uyum sağlamak için programla. Daha yeni hizmetler için sorgular başarısız olursa VSPackage'nız eski sürümlerinde desteklenen diğer hizmetleri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sunabilirsiniz.

- VSPackage'nızı uygun şekilde kaydetme. Daha fazla bilgi için bkz. [VSPackage kaydı](../extensibility/internals/vspackage-registration.md) [ve Yönetilen VSPackage kaydı.](/previous-versions/bb166783(v=vs.100))

- Dosya uzantılarını uygun şekilde kaydedin. Daha fazla bilgi için [bkz. Yan yana dağıtımlar için dosya adı uzantılarını kaydetme.](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)

- VSPackage'ını uygun sürümleri için dağıtan bir yükleyici [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturun. Daha fazla bilgi için, [bkz. Installing VSPackages with Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) and [Component management](../extensibility/internals/component-management.md).

- Kayıt çakışmaları ile ilgili sorunu ele alın. Daha fazla bilgi için bkz. [VSPackage kaydı.](../extensibility/internals/vspackage-registration.md)

- Birden çok sürümün güvenli bir şekilde yüklenmesine ve kaldırılmasına olanak sağlamak için hem paylaşılan hem de sürüme sahip dosyaların başvuru saymaya uygun olduğundan emin olun. Daha fazla bilgi için bkz. [Bileşen yönetimi.](../extensibility/internals/component-management.md)

## <a name="versioned-vspackages"></a>Sürüme Sahip VSPackage'lar
 Sürüme sahip VSPackage stratejisi altında, destekleyenin her sürümü için bir VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturun. Bu, her VSPackage'ın diğerlerini etkilemeden evrim geçirerek daha sonraki sürümleri tarafından sağlanan hizmetlerden yararlanmayı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] beklediğinizde uygundur. Bununla birlikte, tek bir kod tabanından veya birden çok bağımsız kod tabanından birden çok ikili dosya oluşturmanın sürümüne sahip strateji, paylaşılan stratejiden daha fazla ilk geliştirmeyi gerektirir. Ayrıca, her sürüm için ayrı bir kurulum veya yüklü ve VSPackage'nizin desteklediği sürümlerini algılayan tek bir kurulum oluşturmanız gerektiğinden ek kurulum çalışması [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gerekebilir.

## <a name="binary-compatibility"></a>İkili uyumluluk
 Genellikle ikili uyumluluk, önceki Visual Studio sürümleriyle geliştirilen yerel kodLU VSPackage'ların Visual Studio. Ancak üç önemli özel durum vardır:

- VSPackage'nız ortak dil çalışma zamanının belirli bir sürümüne bağlı ise, hangi sürümünün [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çalıştır gerektiğini belirlemesi gerekir.

- VSPackage,başka bir VSPackage'ın veya başka bir ürünün belirli bir özelliğine bağımlı olabilir. Sonuç olarak VSPackage yalnızca bağımlılığın yerine bulunduğu yerde çalışmasına neden olabilir.

- VSPackage, bir hizmet paketi veya sonraki bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sürümündeki bir güvenlik düzeltmesi tarafından etkilenebilir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Böyle durumlarda, güvenlik düzeltmesi uygulandıktan sonra önceki bir sürümüyle geliştirilen VSPackage sürümlerinde [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çalıştırılamayabiliyor. Bununla birlikte, paketinizi sonraki sürümle yeniden yapılandırabilirsiniz ve önceki sürümlerde de çalıştırmanız gerekir.

  Yönetilen VSPackage'lar, ve hedef [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] sürümüyle eşan bir sürümü kullanılarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yerleşiktir.

  VSPackage ikili dosyalarınız için ikili uyumluluğu planlamanın yanı sıra çözüm ve proje dosyası biçimlerini de göz önünde bulundurabilirsiniz. VSPackage'nız yeni bir proje türü oluşturuyorsa, bunun yalnızca bir sürümde mi yoksa birden çok sürümünde mi çalıştırılay olduğuna karar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verebilirsiniz. Daha fazla bilgi için [bkz. Özel projeleri yükseltme.](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Yükleyicisi ile VSPackage'ları Yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Bileşen yönetimi](../extensibility/internals/component-management.md)