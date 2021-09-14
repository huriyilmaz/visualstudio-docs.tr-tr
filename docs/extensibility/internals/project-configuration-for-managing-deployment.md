---
title: Project Dağıtımı yönetme yapılandırması | Microsoft Docs
description: hata ayıklama ve yükleme için beklenen konuma dağıtım hakkında bilgi edinin ve Visual Studio dağıtımı destekleyen projeleri destekler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fdd15349522c1bf49f379551825a773b676f6196
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725027"
---
# <a name="project-configuration-for-managing-deployment"></a>Dağıtımı Yönetmek için Proje Yapılandırması
Dağıtım, çıkış öğelerini bir yapı işleminden fiziksel olarak hata ayıklama ve yükleme için beklenen konuma taşıma işlemidir. Örneğin, bir Web uygulaması yerel bir makinede oluşturulmuş ve sonra sunucuya yerleştirilebilir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , projelerin dağıtıma dahil edilebilir iki yolunu destekler:

- Dağıtım sürecinin konusu.

- Dağıtım işleminin Yöneticisi olarak.

  Çözümlerin dağıtılması için önce dağıtım seçeneklerini yapılandırmak üzere bir dağıtım projesi eklemeniz gerekir. Dağıtım projesi zaten yoksa, **derleme** menüsünden **Çözümü dağıt** ' ı seçtiğinizde bir tane oluşturmak isteyip istemediğiniz sorulur veya çözüme sağ tıklayın. **evet** ' i tıklatmak, **uzak dağıtım sihirbazı** projesi seçiliyken **yeni Project ekle** iletişim kutusunu açar.

  uzak dağıtım sihirbazı sizden uygulama türü (Windows veya Web), dahil edilecek proje çıkış grupları, dahil etmek istediğiniz ek dosyalar ve dağıtmak istediğiniz uzak bilgisayar için size sorar. Sihirbazın son sayfasında, seçilen seçeneklerin bir özeti görüntülenir.

  Bir dağıtım işleminin konusu olan projeler, alternatif bir ortama taşınması gereken çıkış öğeleri oluşturur. Bu çıktı öğeleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , birincil amacı, projelerin çıkışları gruplandırılarına izin versin olan arabirim için parametreler olarak tanımlanır. uygulamasıyla ilgili daha fazla bilgi için `IVsProjectCfg2` bkz. [Project Configuration for Output](../../extensibility/internals/project-configuration-for-output.md).

  Dağıtım işlemini yöneten dağıtım projeleri, Dağıt komutunu etkinleştirir ve bu komut seçildiğinde yanıt verir. Dağıtım projeleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> dağıtımı gerçekleştirmek için arabirimini uygular ve dağıtım <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> durumu olaylarını raporlamak için arabirime çağrı yapar.

  Konfigürasyonlar, derleme veya dağıtım işlemlerini etkileyen bağımlılıklar belirtebilir. Yapı veya dağıtım bağımlılıkları, yapılandırmaların kendilerini oluşturup dağıtmadan önce veya sonra oluşturulması ya da dağıtılması gereken projelerdir. Projeler arasında yapı bağımlılıkları, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> arabirimiyle tanımlanır ve arabirim ile bağımlılıkları dağıtır <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> . daha fazla bilgi için bkz. [derleme için Project yapılandırma](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Derleme için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Çıkış için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-output.md)
