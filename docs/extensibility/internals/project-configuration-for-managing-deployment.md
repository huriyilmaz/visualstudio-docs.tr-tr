---
title: Dağıtımı yönetmeye yönelik proje yapılandırması | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ffa661d8bf33219a3a2956cef3e456c9b5f1146
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726016"
---
# <a name="project-configuration-for-managing-deployment"></a>Dağıtımı Yönetmek için Proje Yapılandırması
Dağıtım, çıkış öğelerini bir yapı işleminden fiziksel olarak hata ayıklama ve yükleme için beklenen konuma taşıma işlemidir. Örneğin, bir Web uygulaması yerel bir makinede oluşturulmuş ve sonra sunucuya yerleştirilebilir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], projelerin dağıtıma dahil edilebilir iki yolunu destekler:

- Dağıtım sürecinin konusu.

- Dağıtım işleminin Yöneticisi olarak.

  Çözümlerin dağıtılması için önce dağıtım seçeneklerini yapılandırmak üzere bir dağıtım projesi eklemeniz gerekir. Dağıtım projesi zaten yoksa, **derleme** menüsünden **Çözümü dağıt** ' ı seçtiğinizde bir tane oluşturmak isteyip istemediğiniz sorulur veya çözüme sağ tıklayın. **Evet** ' i tıklatmak, **uzak dağıtım Sihirbazı** projesi seçiliyken **Yeni Proje Ekle** iletişim kutusunu açar.

  Uzak dağıtım Sihirbazı, uygulama türünü (Windows veya Web), dahil edilecek proje çıkış gruplarını, dahil etmek istediğiniz ek dosyaları ve dağıtmak istediğiniz uzak bilgisayarı belirtmenizi ister. Sihirbazın son sayfasında, seçilen seçeneklerin bir özeti görüntülenir.

  Bir dağıtım işleminin konusu olan projeler, alternatif bir ortama taşınması gereken çıkış öğeleri oluşturur. Bu çıktı öğeleri, projenin çıkışları grupdeğiştirmesine izin vermek için birincil amacı olan <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> arabirimi için parametreler olarak tanımlanır. @No__t_0 uygulamasıyla ilgili daha fazla bilgi için bkz. [çıktı Için proje yapılandırması](../../extensibility/internals/project-configuration-for-output.md).

  Dağıtım işlemini yöneten dağıtım projeleri, Dağıt komutunu etkinleştirir ve bu komut seçildiğinde yanıt verir. Dağıtım projeleri dağıtımı gerçekleştirmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> arabirimini uygular ve dağıtım durumu olaylarını raporlamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> arabirimine çağrı yapar.

  Konfigürasyonlar, derleme veya dağıtım işlemlerini etkileyen bağımlılıklar belirtebilir. Yapı veya dağıtım bağımlılıkları, yapılandırmaların kendilerini oluşturup dağıtmadan önce veya sonra oluşturulması ya da dağıtılması gereken projelerdir. Projeler arasında yapı bağımlılıkları <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> arabirimiyle tanımlanır ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> arabirimiyle bağımlılıkları dağıtır. Daha fazla bilgi için bkz. [derleme Için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Derleme için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Çıkış için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-output.md)