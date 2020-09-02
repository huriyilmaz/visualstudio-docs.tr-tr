---
title: Dağıtımı yönetmeye yönelik proje yapılandırması | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5b16c3392e9432ba540130d45f6907de15b51ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429957"
---
# <a name="project-configuration-for-managing-deployment"></a>Dağıtımı Yönetmek için Proje Yapılandırması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dağıtım, çıkış öğelerini bir yapı işleminden fiziksel olarak hata ayıklama ve yükleme için beklenen konuma taşıma işlemidir. Örneğin, bir Web uygulaması yerel bir makinede oluşturulmuş ve sonra sunucuya yerleştirilebilir.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , projelerin dağıtıma dahil edilebilir iki yolunu destekler:  
  
- Dağıtım sürecinin konusu.  
  
- Dağıtım işleminin Yöneticisi olarak.  
  
  Çözümlerin dağıtılması için önce dağıtım seçeneklerini yapılandırmak üzere bir dağıtım projesi eklemeniz gerekir. Dağıtım projesi zaten yoksa, **derleme** menüsünden **Çözümü dağıt** ' ı seçtiğinizde bir tane oluşturmak isteyip istemediğiniz sorulur veya çözüme sağ tıklayın. **Evet** ' i tıklatmak, **uzak dağıtım Sihirbazı** projesi seçiliyken **Yeni Proje Ekle** iletişim kutusunu açar.  
  
  Uzak dağıtım Sihirbazı, uygulama türünü (Windows veya Web), dahil edilecek proje çıkış gruplarını, dahil etmek istediğiniz ek dosyaları ve dağıtmak istediğiniz uzak bilgisayarı belirtmenizi ister. Sihirbazın son sayfasında, seçilen seçeneklerin bir özeti görüntülenir.  
  
  Bir dağıtım işleminin konusu olan projeler, alternatif bir ortama taşınması gereken çıkış öğeleri oluşturur. Bu çıktı öğeleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , birincil amacı, projelerin çıkışları gruplandırılarına izin versin olan arabirim için parametreler olarak tanımlanır. Uygulamasıyla ilgili daha fazla bilgi için `IVsProjectCfg2` bkz. [çıktı Için proje yapılandırması](../../extensibility/internals/project-configuration-for-output.md).  
  
  Dağıtım işlemini yöneten dağıtım projeleri, Dağıt komutunu etkinleştirir ve bu komut seçildiğinde yanıt verir. Dağıtım projeleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> dağıtımı gerçekleştirmek için arabirimini uygular ve dağıtım <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> durumu olaylarını raporlamak için arabirime çağrı yapar.  
  
  Konfigürasyonlar, derleme veya dağıtım işlemlerini etkileyen bağımlılıklar belirtebilir. Yapı veya dağıtım bağımlılıkları, yapılandırmaların kendilerini oluşturup dağıtmadan önce veya sonra oluşturulması ya da dağıtılması gereken projelerdir. Projeler arasında yapı bağımlılıkları, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> arabirimiyle tanımlanır ve arabirim ile bağımlılıkları dağıtır <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> . Daha fazla bilgi için bkz. [derleme Için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md)   
 [Derleme için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md)   
 [Çıkış için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-output.md)
