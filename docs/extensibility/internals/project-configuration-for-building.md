---
title: Derleme için proje yapılandırması | Microsoft Docs
description: Belirli bir çözüme yönelik çözüm yapılandırmalarının listesinin yeni bir proje türündeki çözüm konfigürasyonları iletişim kutusu tarafından nasıl yönetildiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b817607f765626a6b63693e681306309512fdb7d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074450"
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

 Proje bağımlılıkları ve derleme sırası çözüm yapılandırması bağımsızdır: Yani, Çözümdeki tüm projeler için yalnızca bir bağımlılık ağacı ayarlayabilirsiniz. Çözüme veya projeye sağ tıklayıp **Proje bağımlılıkları** ya da **proje derleme sırası** seçeneğini belirleyerek **Proje bağımlılıkları** iletişim kutusu açılır. Ayrıca, **Proje** menüsünden de açılabilir.

 ![Proje bağımlılıkları](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Proje bağımlılıkları

 Proje bağımlılıkları, projelerin hangi sırada derleyeceğini belirleme. Bir çözümdeki projelerin derolacağı tam sırayı görüntülemek için iletişim kutusundaki derleme sırası sekmesini kullanın ve yapı sırasını değiştirmek için bağımlılıklar sekmesini kullanın.

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
