---
title: Çözüm yapılandırması | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c96b73747ef8b136a74a7256cde7fef8d1c42de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705384"
---
# <a name="solution-configuration"></a>Çözüm Yapılandırması
Çözüm yapılandırması, çözüm düzeyi özellikleri depolar. **Başlat** (F5) anahtar ve **derleme** komutlarının davranışını yönlendirir. Varsayılan olarak, bu komutlar hata ayıklama yapılandırmasını oluşturur ve başlatır. Her iki komut de bir çözüm yapılandırması bağlamında yürütülür. Bu, kullanıcının F5 ' i başlatıp etkin çözümün ayarlar aracılığıyla yapılandırıldığı her şeyi oluşturmasını beklebileceği anlamına gelir. Ortam, oluşturmak ve çalıştırmak için olduğu zaman projeler yerine çözümleri iyileştirmek üzere tasarlanmıştır.

 Standart Visual Studio araç çubuğu, Başlat düğmesinin sağ tarafında bir Başlat düğmesi ve bir çözüm yapılandırması açılır. Bu liste, kullanıcıların F5 tuşuna basıldığında başlatılacak yapılandırmayı seçmesini, kendi çözüm yapılandırmalarını oluşturmayı veya var olan bir yapılandırmayı düzenlemenizi sağlar.

> [!NOTE]
> Çözüm yapılandırması oluşturmaya veya düzenlemeye yönelik bir genişletilebilirlik arabirimi yoktur. Kullanmanız gerekir `DTE.SolutionBuild` . Ancak, çözüm derlemesini yönetmek için genişletilebilirlik API 'Leri vardır. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 İşte, proje türü tarafından desteklenen çözüm yapılandırmalarının nasıl uygulayabileceğinizi aşağıda bulabilirsiniz:

- Project

   Geçerli çözümde bulunan projelerin adlarını görüntüler.

- Yapılandırma

   Proje türü tarafından desteklenen ve özellik sayfalarında görüntülenecek yapılandırmaların listesini sağlamak için uygulamasını uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> .

   Yapılandırma sütunu, bu çözüm yapılandırmasında oluşturulacak proje yapılandırmasının adını görüntüler ve ok düğmesine tıkladığınızda tüm proje yapılandırmalarını listeler. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> Bu listeyi dolduracak şekilde yöntemini çağırır. Yöntemi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> projenin yapılandırma düzenlemesini desteklediğini gösteriyorsa, yapılandırma başlığı altında yeni veya düzenleme seçimleri de görüntülenir. Bu seçimlerin her biri `IVsCfgProvider2` , projenin yapılandırmasını düzenlemek için arabirim yöntemlerini çağıran iletişim kutularını başlatır.

   Bir proje yapılandırmaları desteklemiyorsa, yapılandırma sütunu hiçbiri ' ni görüntüler ve devre dışı bırakılır.

- Platform

   Seçilen proje yapılandırması için platformu görüntüler ve ok düğmesine tıkladığınızda projenin tüm kullanılabilir platformlarını listeler. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> Bu listeyi dolduracak şekilde yöntemini çağırır. Yöntemi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> projenin platform düzenlemesini desteklediğini gösteriyorsa, yeni veya düzenleme seçimleri de platform başlığı altında görüntülenir. Bu seçimlerin her biri `IVsCfgProvider2` , projenin kullanılabilir platformlarını düzenlemek için yöntemler çağıran iletişim kutularını başlatır.

   Bir proje platformları desteklemiyorsa, söz konusu projenin platform sütunu hiçbiri ' ni görüntüler ve devre dışı bırakılır.

- Oluşturma

   Projenin geçerli çözüm yapılandırması tarafından oluşturulup oluşturulmayacağını belirtir. Hiçbir proje bağımlılığı olsa da çözüm düzeyinde derleme komutları çağrıldığında seçilmemiş projeler derlenmez. Derlenmeye seçili olmayan projeler, çözümün hata ayıklaması, çalıştırılması, paketlenmesi ve dağıtılması ile hala dahil edilmiştir.

- Dağıtma

   Başlat veya Dağıt komutları seçili çözüm derleme yapılandırmasıyla kullanıldığında projenin dağıtılıp dağıtılmayacağını belirtir. Bu alanın onay kutusu, proje, arabirimini nesne üzerinde uygulayarak dağıtımı destekliyorsa kullanılabilir olacaktır <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> .

  Yeni bir çözüm yapılandırması eklendikten sonra, Kullanıcı bu yapılandırmayı oluşturmak ve/veya başlatmak için Standart araç çubuğunda çözüm yapılandırması açılan liste kutusundan seçebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Derleme için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Proje Yapılandırması Nesnesi](../../extensibility/internals/project-configuration-object.md)
