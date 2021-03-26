---
title: Paylaşılan ve sürümlü VSPackages arasında seçim yapma | Microsoft Docs
description: Visual Studio 'nun birden çok sürümü ve .NET Framework, paylaşılan veya sürümlü stratejiler aracılığıyla VSPackages 'nin yan yana yüklemeleri hakkında bilgi edinin.
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
ms.workload:
- vssdk
ms.openlocfilehash: 257158ec3c8d4364e1aa52133c457e24fd98cff3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078246"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Paylaşılan ve sürümlenmiş VSPackages arasında seçim yapın
Visual Studio 'nun farklı sürümleri aynı bilgisayarda bulunabilir. VSPackages, sürümlerin herhangi bir karışımını destekleyebilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 Her iki strateji, paylaşılan strateji veya sürümlenmiş strateji aracılığıyla VSPackages 'ın yan yana yüklemelerini etkinleştirebilirsiniz. Her ikisi de .NET Framework birden çok sürümünün [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve ilişkili sürümlerinin varlığına uyum.

 Paylaşılan stratejide, bir VSPackage, uygulamasının birden çok sürümünde kullanılmak üzere kaydedilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Sürümlenmiş stratejide, destekledikleri her sürümü için bir tane olmak üzere birden çok VSPackage dll 'i yüklenmiştir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="shared-vspackages"></a>Paylaşılan VSPackages
 Paylaşılan VSPackage kullanmak, uygulamasının birden çok sürümünde aynı VSPackage kullandığınızda uygundur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Paylaşılan bir VSPackage uygulamak için aşağıdaki adımları uygulamanız gerekir:

- VSPackage 'ın birden fazla sürümüyle uyumlu olmasını sağlayın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Bunu yapmanın iki yolu vardır:

  - VSPackage 'ı yalnızca, destekinizdeki en eski sürümünün özelliklerini kullanarak sınırlayın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  - VSPackage 'ı, çalıştığı sürümünü uyarlayacak şekilde programlayın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Daha sonra, yeni hizmetler için sorgular başarısız olursa, VSPackage daha eski sürümlerinde desteklenen diğer hizmetleri sunabilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- VSPackage 'ı uygun şekilde kaydedin. Daha fazla bilgi için bkz. [VSPackage kaydı](../extensibility/internals/vspackage-registration.md) ve [Yönetilen VSPackage kaydı](/previous-versions/bb166783(v=vs.100)).

- Dosya uzantılarını uygun şekilde kaydedin. Daha fazla bilgi için bkz. [yan yana dağıtımlar için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Uygun sürümleri için VSPackage 'ı dağıtan bir yükleyici oluşturun [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Daha fazla bilgi için bkz. Windows Installer ve [bileşen yönetimi](../extensibility/internals/component-management.md) [Ile VSPackages yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md) .

- Kayıt çakışmaları sorununu çözün. Daha fazla bilgi için bkz. [VSPackage kaydı](../extensibility/internals/vspackage-registration.md).

- Paylaşılan ve sürümlü dosyaların, birden çok sürümün güvenli yüklenmesine ve kaldırılmasına izin vermek için başvuru saydığından emin olun. Daha fazla bilgi için bkz. [bileşen yönetimi](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>Sürümlü VSPackages
 Sürümlenmiş VSPackage stratejisi altında, destekettiğiniz her sürümü için bir VSPackage oluşturacaksınız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Her VSPackage diğerlerini etkilemeden gelişebileceğinden, bu, sonraki sürümlerinde sunulan hizmetlerden yararlanmak istediğinizde uygundur. Bununla birlikte, tek bir kod tabanından veya birden çok bağımsız kod tabanından birden çok ikili dosya oluşturmanın sürümlü stratejisi, paylaşılan stratejisinden daha fazla ilk geliştirmeyi sıraya alabilir. Ayrıca, her sürüm için ayrı bir kurulum veya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklü olan ve VSPackage ' ın desteklediği sürümlerini algılayan tek bir kurulum oluşturmanız gerektiğinden, ek kurulum işi de gerekebilir.

## <a name="binary-compatibility"></a>İkili uyumluluk
 Genellikle ikili uyumluluk, Visual Studio 'nun önceki sürümleriyle geliştirilen yerel kod VSPackages 'i Visual Studio 'nun sonraki sürümlerinde çalışacak şekilde sağlar. Ancak, üç önemli özel durum vardır:

- VSPackage, ortak dil çalışma zamanının belirli bir sürümünü temel alıyorsa, hangi sürümünün çalıştığını belirlememelidir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- VSPackage, başka bir VSPackage veya başka bir ürünün belirli bir özelliğine bağımlılığı olabilir. Sonuç olarak, VSPackage yalnızca bağımlılığın karşılanması durumunda çalıştırılabilir.

- Bir VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , hizmet paketindeki bir güvenlik düzeltmesinin veya daha sonraki bir sürümünde etkileniyor olabilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Bu durumlarda, daha önceki bir sürümüyle geliştirilen VSPackage, [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] güvenlik düzeltmesinin uygulandıktan sonraki sürümlerinde çalıştırılmayabilir. Ancak, paketinizi sonraki sürümle yeniden oluşturabilir ve ayrıca daha önceki sürümlerde çalışmasını sağlayabilirsiniz.

  Yönetilen VSPackages, öğesinin sürümü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve hedef sürümü ile eşleşen bir sürümü kullanılarak oluşturulmalıdır [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  VSPackage ikilileriniz için ikili uyumluluğu planlamaya ek olarak, çözüm ve proje dosya biçimlerini de göz önünde bulundurmanız gerekir. VSPackage yeni bir proje türü oluşturursa, bunun yalnızca bir sürümde mi yoksa birden çok sürümünde mi çalıştırılabileceğine karar vermelisiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Daha fazla bilgi için bkz. [özel projeleri yükseltme](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer ile VSPackages yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Bileşen yönetimi](../extensibility/internals/component-management.md)