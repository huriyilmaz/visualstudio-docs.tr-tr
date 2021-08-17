---
title: Project Oluşturma yapılandırması | Microsoft Docs
description: Belirli bir çözüme yönelik çözüm yapılandırmalarının listesinin yeni bir proje türündeki çözüm konfigürasyonları iletişim kutusu tarafından nasıl yönetildiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 07112d61162f4007db1581c75188295e152e809cd733ff6b3220c5ed1ca742b3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401562"
---
# <a name="project-configuration-for-building"></a>Derleme için Proje Yapılandırması
Belirli bir çözüme yönelik çözüm yapılandırmalarının listesi, çözüm yapılandırması iletişim kutusu tarafından yönetilir.

 Bir Kullanıcı, her biri kendi benzersiz adına sahip ek çözüm konfigürasyonları oluşturabilir. Kullanıcı yeni bir çözüm yapılandırması oluşturduğunda, IDE, projelerde karşılık gelen yapılandırma adını varsayılan olarak alır veya karşılık gelen bir ad yoksa hata ayıklayın. Kullanıcı, gerekirse belirli gereksinimleri karşılamak üzere seçimi değiştirebilir. Bu davranışın tek istisnası, proje yeni çözüm yapılandırmasının adıyla eşleşen bir yapılandırmayı desteklediğinde olur. Örneğin, bir çözümün Project1 ve Project2 içerdiğini varsayalım. Project1, hata ayıklama, perakende ve MyConfig1 proje yapılandırmalarına sahiptir. Project2, hata ayıklama, perakende ve MyConfig2 proje yapılandırmalarına sahiptir.

 Kullanıcı MyConfig2 adlı yeni bir çözüm yapılandırması oluşturmışsa, Project1 hata ayıklama yapılandırmasını varsayılan olarak çözüm yapılandırmasına bağlar. Project2 Ayrıca, MyConfig2 yapılandırmasını varsayılan olarak çözüm yapılandırmasına bağlar.

> [!NOTE]
> Bağlama büyük/küçük harfe duyarlıdır.

 Kullanıcı, yapılandırma açılan listesinde **birden çok seçim** öğesini seçtiğinde, ortam kullanılabilir yapılandırmaların listesini sağlayan bir iletişim kutusu görüntüler.

 ![Birden çok yapılandırma](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Birden çok yapılandırma

 Bu iletişim kutusunda, Kullanıcı bir veya daha fazla yapılandırmayı seçebilir. Seçildiğinde, özellik sayfaları iletişim kutusunda görünen özellik değerleri, seçili yapılandırmaların değerlerinin kesişmesini yansıtır.

 Çözümler ve projeler için yapılandırmaları ekleme ve yeniden adlandırma ile ilgili bilgi için bkz. [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md) .

 Project bağımlılıklar ve derleme siparişi çözüm yapılandırması bağımsızdır: yani, çözümdeki tüm projeler için yalnızca bir bağımlılık ağacı ayarlayabilirsiniz. çözüme veya projeye sağ tıklayıp **Project bağımlılıkları** veya **Project derleme sırası** seçeneğinin belirlenmesi **Project bağımlılıklar** iletişim kutusunu açar. ayrıca, **Project** menüsünden de açılabilir.

 bağımlılıklar Project bağımlılıkları ![Project](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")

 Project bağımlılıklar, projelerin hangi sırada derleyeceğini tespit ediyor. Bir çözümdeki projelerin derolacağı tam sırayı görüntülemek için iletişim kutusundaki derleme sırası sekmesini kullanın ve yapı sırasını değiştirmek için bağımlılıklar sekmesini kullanın.

> [!NOTE]
> Listede onay kutuları seçili, ancak ya da arabirimler tarafından belirtilen açık bağımlılıklar nedeniyle bu ortam tarafından soluk görüntülenen ve değiştirilemeyen bir proje tarafından eklenmiş olan projeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> . Örneğin, bir projeden başka bir projeye bir proje başvurusu eklemek, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] yalnızca başvuru silinerek kaldırılabileceği bir yapı bağımlılığı ekler. Onay kutuları açık ve soluk olarak görünen projeler bir bağımlılık döngüsü oluşturabileceğinden (örneğin, Project1 Project2 'e bağımlı olur ve Project2, Project1 'e bağımlı olur) ve derlemeyi temizler.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yapı işlemleri, tek bir yapı komutuyla çağrılan tipik derleme ve bağlantı işlemlerini içerir. Diğer iki derleme işlemi de desteklenebilir: önceki bir derlemeden tüm çıkış öğelerini silmek için temiz bir işlem ve bir yapılandırmadaki çıkış öğesi değişip değişmediğini tespit etmek için güncel denetim.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> nesneler <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> , derleme süreçlerini yönetmek için karşılık gelen (öğesinden döndürülen) döndürür. Meydana gelen bir yapı işleminin durumunu raporlamak için, yapılandırmaların, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> ortam tarafından uygulanan bir arabirim ve derleme durumu olayları ile ilgilenen diğer herhangi bir nesne için çağrı yapar.

 Oluşturulduktan sonra yapılandırma ayarları, hata ayıklayıcının denetimi altında çalıştırılıp çalıştırılamayacağını anlamak için kullanılabilir. Yapılandırma, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> hata ayıklamayı desteklemek için uygular.

 Proje bağımlılıklarını uyguladıktan sonra, otomasyon modeli aracılığıyla bağımlılıkları programlı bir şekilde değiştirebilirsiniz. <xref:EnvDTE.SolutionBuild.BuildDependencies%2A>Otomasyon modelinde öğesini çağırın. Çözüm yapı Yöneticisi yapılandırmalarının ve bunların özelliklerinin doğrudan işlemesine izin veren kullanılabilir bir VSıP API düzeyi arabirimi yoktur.

 Ayrıca, Proje bağımlılıkları penceresinde bir ızgara sağlayabilirsiniz. Daha fazla bilgi için bkz. [Özellikler görüntüleme Kılavuzu](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Dağıtımı Yönetmek için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Çıkış için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-output.md)
