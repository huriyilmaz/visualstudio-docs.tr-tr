---
title: Dağıtımı yönetmeye yönelik proje yapılandırması | Microsoft Docs
description: Hata ayıklama ve yükleme için beklenen konuma dağıtım ve Visual Studio 'Nun dağıtımı destekleyen projeleri desteklediği iki yolu hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c322e320e193acd25a011cc85173c1c80e2d29d
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877994"
---
# <a name="project-configuration-for-managing-deployment"></a>Dağıtımı Yönetmek için Proje Yapılandırması
Dağıtım, çıkış öğelerini bir yapı işleminden fiziksel olarak hata ayıklama ve yükleme için beklenen konuma taşıma işlemidir. Örneğin, bir Web uygulaması yerel bir makinede oluşturulmuş ve sonra sunucuya yerleştirilebilir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , projelerin dağıtıma dahil edilebilir iki yolunu destekler:

- Dağıtım sürecinin konusu.

- Dağıtım işleminin Yöneticisi olarak.

  Çözümlerin dağıtılması için önce dağıtım seçeneklerini yapılandırmak üzere bir dağıtım projesi eklemeniz gerekir. Dağıtım projesi zaten yoksa, **derleme** menüsünden **Çözümü dağıt** ' ı seçtiğinizde bir tane oluşturmak isteyip istemediğiniz sorulur veya çözüme sağ tıklayın. **Evet** ' i tıklatmak, **uzak dağıtım Sihirbazı** projesi seçiliyken **Yeni Proje Ekle** iletişim kutusunu açar.

  Uzak dağıtım Sihirbazı, uygulama türünü (Windows veya Web), dahil edilecek proje çıkış gruplarını, dahil etmek istediğiniz ek dosyaları ve dağıtmak istediğiniz uzak bilgisayarı belirtmenizi ister. Sihirbazın son sayfasında, seçilen seçeneklerin bir özeti görüntülenir.

  Bir dağıtım işleminin konusu olan projeler, alternatif bir ortama taşınması gereken çıkış öğeleri oluşturur. Bu çıktı öğeleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , birincil amacı, projelerin çıkışları gruplandırılarına izin versin olan arabirim için parametreler olarak tanımlanır. Uygulamasıyla ilgili daha fazla bilgi için `IVsProjectCfg2` bkz. [çıktı Için proje yapılandırması](../../extensibility/internals/project-configuration-for-output.md).

  Dağıtım işlemini yöneten dağıtım projeleri, Dağıt komutunu etkinleştirir ve bu komut seçildiğinde yanıt verir. Dağıtım projeleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> dağıtımı gerçekleştirmek için arabirimini uygular ve dağıtım <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> durumu olaylarını raporlamak için arabirime çağrı yapar.

  Konfigürasyonlar, derleme veya dağıtım işlemlerini etkileyen bağımlılıklar belirtebilir. Yapı veya dağıtım bağımlılıkları, yapılandırmaların kendilerini oluşturup dağıtmadan önce veya sonra oluşturulması ya da dağıtılması gereken projelerdir. Projeler arasında yapı bağımlılıkları, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> arabirimiyle tanımlanır ve arabirim ile bağımlılıkları dağıtır <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> . Daha fazla bilgi için bkz. [derleme Için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Derleme için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Çıkış için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-output.md)
