---
title: Bina için Proje Yapılandırması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd084053e06206a99298b234b4d51c8504119a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706737"
---
# <a name="project-configuration-for-building"></a>Derleme için Proje Yapılandırması
Belirli bir çözüm için çözüm yapılandırmaları listesi Çözüm Yapılandırmaları iletişim kutusu tarafından yönetilir.

 Bir kullanıcı, her biri kendi benzersiz adı olan ek çözüm yapılandırmaları oluşturabilir. Kullanıcı yeni bir çözüm yapılandırması oluşturduğunda, IDE projelerdeki karşılık gelen yapılandırma adına varsayılan olarak veya karşılık gelen ad yoksa hata ayıklama. Kullanıcı gerekirse belirli gereksinimleri karşılamak için seçimi değiştirebilir. Bu davranışın tek istisnası, projenin yeni çözüm yapılandırmasının adıyla eşleşen bir yapılandırmayı desteklemesidir. Örneğin, bir çözüm Project1 ve Project2 içerir varsayalım. Project1'de Hata Ayıklama, Perakende ve MyConfig1 proje yapılandırmaları vardır. Project2'de Hata Ayıklama, Perakende ve MyConfig2 proje yapılandırmaları vardır.

 Kullanıcı MyConfig2 adında yeni bir çözüm yapılandırması oluşturursa, Project1 hata ayıklama yapılandırmasını varsayılan olarak çözüm yapılandırmasına bağlar. Project2 ayrıca MyConfig2 yapılandırmasını varsayılan olarak çözüm yapılandırmasına bağlar.

> [!NOTE]
> Bağlama büyük/küçük harf duyarsızlığıdır.

 Kullanıcı yapılandırma açılır listesinde **Çoklu Seçim** öğesini seçtiğinde, ortam kullanılabilir yapılandırmaların listesini sağlayan bir iletişim kutusu görüntüler.

 ![Birden Çok Yapılandırma](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Birden çok yapılandırma

 Bu iletişim kutusu içinde, kullanıcı bir veya birden çok yapılandırma seçebilir. Seçildikten sonra, özellik sayfaları iletişim kutusunda görüntülenen özellik değerleri, seçili yapılandırmalar için değerlerin kesişimini yansıtır.

 Çözümler ve projeler için yapılandırma ekleme ve yeniden adlandırma ile ilgili bilgiler için [Çözüm Yapılandırması'na](../../extensibility/internals/solution-configuration.md) bakın.

 Proje bağımlılıkları ve yapı düzeni çözüm yapılandırması bağımsızdır: yani çözümdeki tüm projeler için yalnızca bir bağımlılık ağacı ayarlayabilirsiniz. Çözüme veya projeye sağ tıklayıp **Proje Bağımlılıkları** veya **Proje Oluşturma Sırası** seçeneğini **seçmek, Proje Bağımlılıkları** iletişim kutusunu açar. **Proje** menüsünden de açılabilir.

 ![Proje Bağımlılıkları](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Proje bağımlılıkları

 Proje bağımlılıkları, projelerin oluşturma sırasını belirler. Bir çözümdeki projelerin tam olarak oluşturacağı sırayı görüntülemek için iletişim kutusundaki Yapı Sırası sekmesini kullanın ve yapı sırasını değiştirmek için Bağımlılıklar sekmesini kullanın.

> [!NOTE]
> Listedeki onay kutularını seçili ancak soluk görünen projeler, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> arabirimler tarafından belirtilen açık bağımlılıklar nedeniyle ortam tarafından eklenmiştir ve değiştirilemez. Örneğin, projeden başka bir [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projeye proje başvurusu eklemek, yalnızca başvuruyu silerek kaldırılabilen bir yapı bağımlılığı nı otomatik olarak ekler. Onay kutuları açık olan ve soluk görünen projeler seçilemez, çünkü bunu yapmak bir bağımlılık döngüsü oluşturur (örneğin, Project1 Project2'ye bağımlı olur ve Project2, yapıyı durduracak Project1'e bağımlı olur).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]yapı işlemleri, tek bir Yapı komutuyla çağrılan tipik derleme ve bağlantı işlemlerini içerir. Diğer iki yapı işlemi de desteklenebilir: önceki bir yapıdaki tüm çıktı öğelerini silmek için temiz bir işlem ve yapılandırmadaki bir çıktı öğesinin değişip değişmediğini belirlemek için güncel bir denetim.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>nesneler, yapı <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> süreçlerini <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>yönetmek için karşılık gelen (döndürülen) döndürür. Bir yapı işleminin durumunu oluştururken bildirmek için, yapılandırmalar ortam tarafından uygulanan bir arabirim ve yapı durumu olaylarıyla ilgilenen diğer nesnelere <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>çağrı yapar.

 Bir kez kurulduktan sonra, yapılandırma ayarları hata ayıklayıcının denetimi altında çalıştırılıp çalıştırılamayacaklarını belirlemek için kullanılabilir. Yapılandırmalar <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> hata ayıklama desteklemek için uygular.

 Proje bağımlılıklarını uyguladıktan sonra, otomasyon modeli aracılığıyla bağımlılıkları programlı bir şekilde işleyebilirsiniz. Otomasyon <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> modelini çağırıyorsun. Çözüm yapı yöneticisi yapılandırmalarının ve özelliklerinin doğrudan manipülasyonuna izin veren mevcut VSIP API düzeyinde arabirimler yoktur.

 Ayrıca, proje bağımlılıkları penceresinde bir ızgara sağlayabilirsiniz. Daha fazla bilgi için Bkz. [Özellikler Görüntü Kılavuz.](../../extensibility/internals/properties-display-grid.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Dağıtımı Yönetmek için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Çıkış için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-output.md)
