---
title: Project Dağıtım Yönetim Yapılandırması | Microsoft Docs
description: Hata ayıklama ve yükleme için beklenen konuma dağıtım hakkında bilgi ve dağıtımı destekleyen projeleri Visual Studio iki yolu hakkında bilgi edinebilirsiniz.
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
ms.openlocfilehash: aa66bd9e4760c060082c07d72a90f853bf47dbda3604016b8786fb105fbaac4d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375717"
---
# <a name="project-configuration-for-managing-deployment"></a>Dağıtımı Yönetmek için Proje Yapılandırması
Dağıtım, çıkış öğelerini derleme sürecinden hata ayıklama ve yükleme için beklenen konuma fiziksel olarak taşıma eylemidir. Örneğin, bir Web uygulaması yerel bir makine üzerinde ve ardından sunucuya yerleştirilmiş olabilir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projelerin dağıtıma dahil olması için iki yolu destekler:

- Dağıtım işleminin konusu olarak.

- Dağıtım işleminin yöneticisi olarak.

  Çözümlerin dağıtılabilir olması için önce dağıtım seçeneklerini yapılandırmak üzere bir dağıtım projesi eklemeniz gerekir. Dağıtım projesi zaten mevcutsa, Derleme menüsünden Çözümü Dağıt'ı  seçerek veya  çözüme sağ tıklarsanız bir tane oluşturmak istediğiniz soruldu. **Evet'e** **tıklamak, Uzaktan Project** Sihirbazı projesinin seçili olduğu Yeni Uygulama **Ekle iletişim** kutusunu açar.

  Uzaktan Dağıtma Sihirbazı sizden uygulama türünü (Windows veya Web), dahil etmek istediğiniz proje çıkış gruplarını, dahil etmek istediğiniz ek dosyaları ve dağıtmak istediğiniz uzak bilgisayarı ister. Sihirbazın son sayfasında, seçilen seçeneklerin özeti görüntülenir.

  Dağıtım işleminin konusu olan projeler, alternatif bir ortama taşınmaları gereken çıkış öğeleri üretir. Bu çıkış öğeleri, projelerin çıkışları gruplatırmalarına izin vermek için birincil amacı olan <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> arabirim için parametreler olarak açıklanmıştır. uygulamasıyla ilgili daha fazla bilgi için `IVsProjectCfg2` bkz. [Project Için Yapılandırma.](../../extensibility/internals/project-configuration-for-output.md)

  Dağıtım işlemini yöneten dağıtım projeleri, Dağıt komutunu etkinleştirin ve bu komut seçildiğinde yanıt verin. Dağıtım projeleri, dağıtımı <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> gerçekleştirmek ve dağıtım durumu olaylarını rapor etmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> arabirime çağrılar yapmak için arabirimini kullanır.

  Yapılandırmalar, derleme veya dağıtım işlemlerini etkileyen bağımlılıkları belirtebilirsiniz. Derleme veya dağıtma bağımlılıkları, yapılandırmaların kendileri oluşturmadan veya dağıtmadan önce veya dağıtıldıktan sonra ya da oluşturmadan önce dağıtılması gereken projelerdir. Projeler arasındaki derleme bağımlılıkları arabirimiyle <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> açıklanmıştır ve arabirimle bağımlılıkları <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> dağıtır. Daha fazla bilgi için [bkz. Project Yapılandırma.](../../extensibility/internals/project-configuration-for-building.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Derleme için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Çıkış için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-output.md)
