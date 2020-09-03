---
title: Paylaşılan ve sürümlü VSPackages arasında seçim yapma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 289e506d3cd404bba9a3a63d97179b89a948d381
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821973"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Paylaşılan ve Sürümü Tutulan VSPackage’lar Arasında Seçim Yapma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'nun farklı sürümleri aynı bilgisayarda bulunabilir. VSPackages, sürümlerin herhangi bir karışımını destekleyebilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Her iki strateji, paylaşılan strateji veya sürümlenmiş strateji aracılığıyla VSPackages 'ın yan yana yüklemelerini etkinleştirebilirsiniz. Her ikisi de uygulamasının birden çok sürümünün [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve ilişkili sürümlerinin varlığına uyum [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 Paylaşılan stratejide, bir VSPackage, uygulamasının birden çok sürümünde kullanılmak üzere kaydedilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Sürümlenmiş stratejide, destekledikleri her sürümü için bir tane olmak üzere birden çok VSPackage dll 'i yüklenmiştir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="shared-vspackages"></a>Paylaşılan VSPackages  
 Paylaşılan VSPackage kullanmak, uygulamasının birden çok sürümünde aynı VSPackage kullandığınızda uygundur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Paylaşılan bir VSPackage uygulamak için aşağıdaki adımları uygulamanız gerekir:  
  
- VSPackage 'ın birden fazla sürümüyle uyumlu olmasını sağlayın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Bunu yapmanın iki yolu vardır:  
  
  - VSPackage 'ı yalnızca, destekinizdeki en eski sürümünün özelliklerini kullanarak sınırlayın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  

  - VSPackage 'ı, çalıştığı sürümünü uyarlayacak şekilde programlayın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Daha sonra, yeni hizmetler için sorgular başarısız olursa, VSPackage daha eski sürümlerinde desteklenen diğer hizmetleri sunabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- VSPackage 'ı uygun şekilde kaydedin. Daha fazla bilgi için bkz. [VSPackage kaydı](../extensibility/internals/vspackage-registration.md) ve [Yönetilen VSPackage kaydı](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
- Dosya uzantılarını uygun şekilde kaydedin. Daha fazla bilgi için bkz. [yan yana dağıtımlar Için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
- Uygun sürümleri için VSPackage 'ı dağıtan bir yükleyici oluşturun [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Daha fazla bilgi için bkz. Windows Installer ve [bileşen yönetimi](../extensibility/internals/component-management.md) [Ile VSPackages yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md) .  
  
- Kayıt çakışmaları sorununu çözün. Daha fazla bilgi için bkz. [VSPackage kaydı](../extensibility/internals/vspackage-registration.md).  
  
- Paylaşılan ve sürümlü dosyaların, birden çok sürümün güvenli yüklenmesine ve kaldırılmasına izin vermek için başvuru saydığından emin olun. Daha fazla bilgi için bkz. [bileşen yönetimi](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Sürümlü VSPackages  
 Sürümlenmiş VSPackage stratejisi altında, destekettiğiniz her sürümü için bir VSPackage oluşturacaksınız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Her VSPackage diğerlerini etkilemeden gelişebileceğinden, bu, sonraki sürümlerinde sunulan hizmetlerden yararlanmak istediğinizde uygundur. Bununla birlikte, tek bir kod tabanından veya birden çok bağımsız kod tabanından birden çok ikili dosya oluşturmanın sürümlü stratejisi, paylaşılan stratejisinden daha fazla ilk geliştirmeyi sıraya alabilir. Ayrıca, her sürüm için ayrı bir kurulum veya [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yüklü olan ve VSPackage ' ın desteklediği sürümlerini algılayan tek bir kurulum oluşturmanız gerektiğinden, ek kurulum işi de gerekebilir.  
  
## <a name="binary-compatibility"></a>İkili uyumluluk  
 Genellikle ikili uyumluluk, Visual Studio 'nun önceki sürümleriyle geliştirilen yerel kod VSPackages 'i Visual Studio 'nun sonraki sürümlerinde çalışacak şekilde sağlar. Ancak, üç önemli özel durum vardır:  
  
- VSPackage, ortak dil çalışma zamanının belirli bir sürümünü temel alıyorsa, hangi sürümünün çalıştığını belirlememelidir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- VSPackage, başka bir VSPackage veya başka bir ürünün belirli bir özelliğine bağımlılığı olabilir. Sonuç olarak, VSPackage yalnızca bağımlılığın karşılanması durumunda çalıştırılabilir.  
  
- Bir VSPackage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , hizmet paketindeki bir güvenlik düzeltmesinin veya daha sonraki bir sürümünde etkileniyor olabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Bu durumlarda, daha önceki bir sürümüyle geliştirilen VSPackage, [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] güvenlik düzeltmesinin uygulandıktan sonraki sürümlerinde çalıştırılmayabilir. Ancak, paketinizi sonraki sürümle yeniden oluşturabilir ve ayrıca daha önceki sürümlerde çalışmasını sağlayabilirsiniz.  
  
  Yönetilen VSPackages, öğesinin sürümü [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve hedef sürümü ile eşleşen bir sürümü kullanılarak oluşturulmalıdır [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
  VSPackage ikilileriniz için ikili uyumluluğu planlamaya ek olarak, çözüm ve proje dosya biçimlerini de göz önünde bulundurmanız gerekir. VSPackage yeni bir proje türü oluşturursa, bunun yalnızca bir sürümde mi yoksa birden çok sürümünde mi çalıştırılabileceğine karar vermelisiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Daha fazla bilgi için bkz. [özel projeleri yükseltme](../misc/upgrading-custom-projects.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Installer Ile VSPackages yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Bileşen Yönetimi](../extensibility/internals/component-management.md)
