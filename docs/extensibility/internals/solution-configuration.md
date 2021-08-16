---
title: Çözüm yapılandırması | Microsoft Docs
description: Başlangıç (F5) anahtar ve derleme komutlarının davranışını yönlendirerek, proje türü tarafından desteklenen çözüm yapılandırmalarının nasıl uygulanacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2b7a3cb329c6e9e14dd06ff1e82c42563f06624f13d64afd8217f5931be86e7e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414408"
---
# <a name="solution-configuration"></a>Çözüm Yapılandırması
Çözüm yapılandırması, çözüm düzeyi özellikleri depolar. **Başlat** (F5) anahtar ve **derleme** komutlarının davranışını yönlendirir. Varsayılan olarak, bu komutlar hata ayıklama yapılandırmasını oluşturur ve başlatır. Her iki komut de bir çözüm yapılandırması bağlamında yürütülür. Bu, kullanıcının F5 ' i başlatıp etkin çözümün ayarlar aracılığıyla yapılandırıldığı her şeyi oluşturmasını beklebileceği anlamına gelir. Ortam, oluşturmak ve çalıştırmak için olduğu zaman projeler yerine çözümleri iyileştirmek üzere tasarlanmıştır.

 standart Visual Studio araç çubuğu, başlat düğmesinin sağ tarafında bir başlat düğmesi ve bir çözüm yapılandırması açılır. Bu liste, kullanıcıların F5 tuşuna basıldığında başlatılacak yapılandırmayı seçmesini, kendi çözüm yapılandırmalarını oluşturmayı veya var olan bir yapılandırmayı düzenlemenizi sağlar.

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
