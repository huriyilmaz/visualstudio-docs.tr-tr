---
title: Çözüm Yapılandırması | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705384"
---
# <a name="solution-configuration"></a>Çözüm Yapılandırması
Çözüm yapılandırmaları çözüm düzeyinde özellikleri depolar. **Başlat** (F5) tuşu ve **Build** komutlarının davranışını yönlendirirler. Varsayılan olarak, bu komutlar hata ayıklama yapılandırmasını oluşturur ve başlatın. Her iki komut da çözüm yapılandırması bağlamında yürütülür. Bu, kullanıcının F5'in etkin çözüm ayarları aracılığıyla yapılandırıldığında niçin başlatılmasını ve oluşturulmasını bekleyebileceği anlamına gelir. Çevre, bina ve işletme söz konusu olduğunda projelerden çok çözümler için optimize etmek üzere tasarlanmıştır.

 Standart Visual Studio araç çubuğu, Başlat düğmesinin sağında bir Başlat düğmesi ve bir çözüm yapılandırması açılır içerir. Bu liste, kullanıcıların F5 tuşuna basıldığında başlatma yapılandırmasını seçmelerine, kendi çözüm yapılandırmalarını oluşturmalarına veya varolan bir yapılandırmayı düzenlemelerine olanak tanır.

> [!NOTE]
> Çözüm yapılandırmaları oluşturmak veya düzenlemek için genişletilebilirlik arabirimleri yoktur. `DTE.SolutionBuild`Kullanmalısın. Ancak, çözüm oluşturma yönetmek için genişletilebilirlik API'leri vardır. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 Proje türünüz tarafından desteklenen çözüm yapılandırmalarını şu şekilde uygulayabilirsiniz:

- Project

   Geçerli çözümde bulunan projelerin adlarını görüntüler.

- Yapılandırma

   Proje türünüz tarafından desteklenen ve özellik sayfalarında görüntülenen yapılandırmaların listesini <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>sağlamak için uygulayın.

   Yapılandırma sütunu, bu çözüm yapılandırmasında oluşturmak üzere proje yapılandırmasının adını görüntüler ve ok düğmesini tıklattığınızda tüm proje yapılandırmalarını listeler. Ortam, bu <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> listeyi doldurmak için yöntemi çağırır. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> Yöntem, projenin yapılandırma düzenlemesini desteklediğini gösteriyorsa, Yapılandırma başlığı altında Yeni veya Düzenle seçimleri de görüntülenir. Bu seçimlerin her biri, projenin yapılandırmalarını `IVsCfgProvider2` düzenlemek için arabirimin yöntemlerini arayan iletişim kutularını başlatır.

   Proje yapılandırmaları desteklemiyorsa, Yapılandırma sütunu Yok'u görüntüler ve devre dışı bırakılır.

- Platform

   Seçili proje yapılandırmasının oluşturduğu platformu görüntüler ve ok düğmesini tıklattığınızda proje için kullanılabilir tüm platformları listeler. Ortam, bu <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> listeyi doldurmak için yöntemi çağırır. Yöntem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> projenin platform düzenlemeyi desteklediğini gösteriyorsa, Platform başlığı altında Yeni veya Düzenle seçimleri de görüntülenir. Bu seçimlerin her biri, projenin `IVsCfgProvider2` kullanılabilir platformlarını düzenlemek için yöntemleri arayan iletişim kutularını başlatır.

   Proje platformları desteklemiyorsa, bu projenin platform sütunu Yok'u görüntüler ve devre dışı bırakılır.

- Yapı

   Projenin geçerli çözüm yapılandırması tarafından oluşturulup oluşturulmadığını belirtir. Çözüm düzeyindeki yapı komutları içerdikleri proje bağımlılıklarına rağmen çağrıldıklarında seçili olmayan projeler oluşturulmaz. Oluşturulacak şekilde seçilmemiş projeler hala hata ayıklama, çalıştırma, paketleme ve çözümün dağıtımına dahildir.

- Dağıtma

   Seçili çözüm yapı yapılandırmasıyla Başlat veya Dağıt komutları kullanıldığında projenin dağıtılıp dağıtılmayacağını belirtir. Proje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> nesnesi üzerinde arabirimi uygulayarak dağıtımı destekliyorsa, bu alanın onay kutusu kullanılabilir.

  Yeni bir çözüm yapılandırması eklendikten sonra, kullanıcı bu yapılandırmayı oluşturmak ve/veya başlatmak için standart araç çubuğundaki Çözüm Yapılandırma açılır liste kutusundan seçebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Derleme için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Proje Yapılandırması Nesnesi](../../extensibility/internals/project-configuration-object.md)
