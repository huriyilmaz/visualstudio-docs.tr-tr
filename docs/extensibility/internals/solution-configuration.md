---
title: Çözüm yapılandırması | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 243af2549862f1d29c44ba5bfc3060d87d5c6f85
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723840"
---
# <a name="solution-configuration"></a>Çözüm Yapılandırması
Çözüm yapılandırması, çözüm düzeyi özellikleri depolar. **Başlat** (F5) anahtar ve **derleme** komutlarının davranışını yönlendirir. Varsayılan olarak, bu komutlar hata ayıklama yapılandırmasını oluşturur ve başlatır. Her iki komut de bir çözüm yapılandırması bağlamında yürütülür. Bu, kullanıcının F5 ' i başlatıp etkin çözümün ayarlar aracılığıyla yapılandırıldığı her şeyi oluşturmasını beklebileceği anlamına gelir. Ortam, oluşturmak ve çalıştırmak için olduğu zaman projeler yerine çözümleri iyileştirmek üzere tasarlanmıştır.

 Standart Visual Studio araç çubuğu, Başlat düğmesinin sağ tarafında bir Başlat düğmesi ve bir çözüm yapılandırması açılır. Bu liste, kullanıcıların F5 tuşuna basıldığında başlatılacak yapılandırmayı seçmesini, kendi çözüm yapılandırmalarını oluşturmayı veya var olan bir yapılandırmayı düzenlemenizi sağlar.

> [!NOTE]
> Çözüm yapılandırması oluşturmaya veya düzenlemeye yönelik bir genişletilebilirlik arabirimi yoktur. @No__t_0 kullanmanız gerekir. Ancak, çözüm derlemesini yönetmek için genişletilebilirlik API 'Leri vardır. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 İşte, proje türü tarafından desteklenen çözüm yapılandırmalarının nasıl uygulayabileceğinizi aşağıda bulabilirsiniz:

- Project

   Geçerli çözümde bulunan projelerin adlarını görüntüler.

- Yapılandırma

   Proje türü tarafından desteklenen ve özellik sayfalarında görüntülenecek yapılandırmaların listesini sağlamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> uygulayın.

   Yapılandırma sütunu, bu çözüm yapılandırmasında oluşturulacak proje yapılandırmasının adını görüntüler ve ok düğmesine tıkladığınızda tüm proje yapılandırmalarını listeler. Ortam, bu listeyi dolduracak <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> yöntemini çağırır. @No__t_0 yöntemi projenin yapılandırma düzenlemesini desteklediğini gösteriyorsa, yapılandırma başlığı altında yeni veya düzenleme seçimleri de görüntülenir. Bu seçimlerin her biri, projenin yapılandırmasını düzenlemek için `IVsCfgProvider2` arabiriminin yöntemlerini çağıran iletişim kutularını başlatır.

   Bir proje yapılandırmaları desteklemiyorsa, yapılandırma sütunu hiçbiri ' ni görüntüler ve devre dışı bırakılır.

- Platform

   Seçilen proje yapılandırması için platformu görüntüler ve ok düğmesine tıkladığınızda projenin tüm kullanılabilir platformlarını listeler. Ortam, bu listeyi dolduracak <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> yöntemini çağırır. @No__t_0 yöntemi, projenin platform düzenlemesini desteklediğini gösteriyorsa, yeni veya düzenleme seçimleri de platform başlığı altında görüntülenir. Bu seçimlerin her biri, projenin kullanılabilir platformlarını düzenlemek için `IVsCfgProvider2` Yöntemler çağıran iletişim kutularını başlatır.

   Bir proje platformları desteklemiyorsa, söz konusu projenin platform sütunu hiçbiri ' ni görüntüler ve devre dışı bırakılır.

- Yapı

   Projenin geçerli çözüm yapılandırması tarafından oluşturulup oluşturulmayacağını belirtir. Hiçbir proje bağımlılığı olsa da çözüm düzeyinde derleme komutları çağrıldığında seçilmemiş projeler derlenmez. Derlenmeye seçili olmayan projeler, çözümün hata ayıklaması, çalıştırılması, paketlenmesi ve dağıtılması ile hala dahil edilmiştir.

- Dağıt

   Başlat veya Dağıt komutları seçili çözüm derleme yapılandırmasıyla kullanıldığında projenin dağıtılıp dağıtılmayacağını belirtir. Bu alanın onay kutusu, proje dağıtımı destekliyorsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> nesnesinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> arabirimini uygulamayı destekliyorsa kullanılabilir.

  Yeni bir çözüm yapılandırması eklendikten sonra, Kullanıcı bu yapılandırmayı oluşturmak ve/veya başlatmak için Standart araç çubuğunda çözüm yapılandırması açılan liste kutusundan seçebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Derleme için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Proje Yapılandırması Nesnesi](../../extensibility/internals/project-configuration-object.md)