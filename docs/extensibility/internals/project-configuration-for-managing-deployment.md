---
title: Dağıtım Yönetimi için Proje Yapılandırması | Microsoft Dokümanlar
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
ms.openlocfilehash: 62f7bf6535a89e46799ade88fe8976974b3019c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706707"
---
# <a name="project-configuration-for-managing-deployment"></a>Dağıtımı Yönetmek için Proje Yapılandırması
Dağıtım, çıktı maddelerini bir yapı işleminden hata ayıklama ve yükleme için beklenen konuma fiziksel olarak taşıma eylemidir. Örneğin, bir Web uygulaması yerel bir makinede oluşturulabilir ve sunucuya yerleştirilebilir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]projelerin dağıtımda yer alabildiği iki yolu destekler:

- Dağıtım sürecinin konusu olarak.

- Dağıtım işleminin yöneticisi olarak.

  Çözümler dağıtılmadan önce, dağıtım seçeneklerini yapılandırmak için önce bir dağıtım projesi eklemeniz gerekir. Dağıtma projesi zaten yoksa, **Yapı** menüsünden **Çözüm Dağı'nı** seçtiğinizde veya çözüme sağ tıklattığınızda bir tane oluşturmak isteyip istemediğiniz sorulur. **Evet'i** tıklattığınızda, **Seçili Uzaktan Dağıtma Sihirbazı** projesiyle **Yeni Proje Ekle** iletişim kutusunu açar.

  Uzaktan Dağıtma Sihirbazı sizden uygulama türünü (Windows veya Web), proje çıktı gruplarını, eklemek istediğiniz ek dosyaları ve dağıtmak istediğiniz uzak bilgisayarı ister. Sihirbazın son sayfası seçili seçeneklerin bir özetini görüntüler.

  Dağıtım işleminin konusu olan projeler, alternatif bir ortama taşınması gereken çıktı öğeleri üretir. Bu çıktı öğeleri, projelerin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> çıktıları gruplandırmasına izin vermek birincil amacı olan arabirim için parametreler olarak tanımlanır. Uygulama ile ilgili daha `IVsProjectCfg2`fazla bilgi [için, Çıktı için Proje](../../extensibility/internals/project-configuration-for-output.md)Yapılandırması'na bakın.

  Dağıtım işlemini yöneten dağıtım projeleri, Dağıtım komutunu etkinleştirin ve bu komut seçildiğinde yanıt verir. Dağıtım projeleri, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> dağıtımı gerçekleştirmek için arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> uygular ve durum durum olaylarını bildirmek için arabirime çağrı yapar.

  Yapılandırmalar, yapı veya dağıtım işlemlerini etkileyen bağımlılıkları belirtebilir. Yapı veya dağıtma bağımlılıkları, yapılandırmalar oluşturulmadan veya dağıtıldıktan önce veya sonra oluşturulması veya dağıtılması gereken projelerdir. Projeler arasındaki bağımlılıkları oluşturma <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> arabirimi ile açıklanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> ve arabirim ile bağımlılıkları dağıtılır. Daha fazla bilgi [için, Bina için Proje Yapılandırması'na](../../extensibility/internals/project-configuration-for-building.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Derleme için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Çıkış için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-output.md)
