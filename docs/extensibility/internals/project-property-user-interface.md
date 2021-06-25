---
title: Proje Özelliği Kullanıcı Arabirimi | Microsoft Docs
description: Proje alt türlerinden, temel proje tarafından sağlanan proje Özellik Sayfaları iletişim kutusunu nasıl değiştiryebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77e3554f2a3fd3b0dc1d608bb7d0a1198116a4e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903595"
---
# <a name="project-property-user-interface"></a>Proje Özelliği Kullanıcı Arabirimi

Bir proje alt türü, temel  proje tarafından sağlanan şekilde proje Özellik Sayfaları iletişim kutusundaki öğeleri kullanabilir, sağlanan şekilde salt okunur denetimleri ve tam  sayfaları gizler veya oluşturabilir ya da Özellik Sayfaları iletişim kutusuna proje alt türüne özgü sayfalar ekleyebilir.

## <a name="extending-the-project-property-dialog-box"></a>Proje Özelliğini Genişletme İletişim Kutusu

Proje alt türü otomasyon genişleticileri ve proje yapılandırması göz atma nesnelerini kullanır. Bu genişleticiler, <xref:EnvDTE.IFilterProperties> belirli özellikleri gizli veya salt okunur yapmak için arabirimini uygulamaya ekler. Temel **proje** tarafından uygulanan temel projenin Özellik Sayfaları iletişim kutusu, Otomasyon Genişleticileri tarafından gerçekleştirilen filtrelemeye onaylar.

Proje Özelliği iletişim kutusunu **genişletme** işlemi aşağıda özetlenmiştir:

- Temel proje, arabirimini kullanarak proje alt türünden genişleticileri <xref:EnvDTE80.IInternalExtenderProvider> alın. Temel projenin göz atma, proje otomasyonu ve proje yapılandırması göz atma nesneleri bu arabirimi kullanır.

- proje göz atma nesnesi için uygulaması ve proje otomasyonu nesnesi, proje alt türü toplayıcısı <xref:EnvDTE80.IInternalExtenderProvider> uygulamasına (yani, proje nesnesinde için) <xref:EnvDTE80.IInternalExtenderProvider> `QueryInterface` temsilci olarak temsil <xref:EnvDTE80.IInternalExtenderProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> eder.

- Temel proje yapılandırması göz atma nesnesi, proje alt türü yapılandırma nesnesinden <xref:EnvDTE80.IInternalExtenderProvider> Otomasyon Genişleticisi'ne doğrudan kablo eklemek için de uygulanır. Uygulaması, proje alt <xref:EnvDTE80.IInternalExtenderProvider> türü toplayıcısı tarafından uygulanan arabirime temsilci olarak görev gösterir.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, proje yapılandırması gözatma nesnesi tarafından uygulanan nesnesini <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> döndürür.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, ayrıca proje yapılandırması gözatma nesnesi tarafından uygulanan nesnesini <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> döndürür.

- Bir proje alt türü, aşağıdaki değerleri alarak çalışma zamanında temel projenin çeşitli değiştirilebilir nesneleri için uygun CATID'leri <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> belirler:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Proje kapsamı için CATID'leri belirlemek üzere, proje alt türü VSITEMID için yukarıdaki [özellikleri almaktadır. kökünden.](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) `VSITEMID typedef` Proje alt türü, hem yapılandırmaya bağımlı hem de yapılandırmadan bağımsız olarak proje için hangi Özellik Sayfaları iletişim kutusu sayfalarının görüntülendiğinden emin olmak istiyor olabilir.  Bazı proje alt türlerinden yerleşik sayfaları kaldırması ve proje alt türüne özgü sayfalar eklemesi gerekir. Bunu etkinleştirmek için, yönetilen istemci projesi aşağıdaki özellikler <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> için yöntemini çağırtır:

- `VSHPROPID_PropertyPagesCLSIDList` — yapılandırmadan bağımsız özellik sayfalarının CLSID'lerinin noktalı virgülle ayrılmış listesi.

- `VSHPROPID_CfgPropertyPagesCLSIDList —` yapılandırmaya bağımlı özellik sayfalarının CLSID'lerinin noktalı virgülle ayrılmış listesi.

Proje alt türü nesneyi toplasa da, hangi Özellik Sayfaları iletişim kutularının görüntülendiğinden emin olmak <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> için bu özelliklerin **tanımını** geçersiz kılamaz. Proje alt türü, bu özellikleri iç temel projeden alabilir ve ardından gerektiğinde CLSID'leri ekleyebilir veya kaldırabilir.

Bir proje alt türü tarafından eklenen yeni özellik sayfalarına, temel proje uygulamasından bir proje yapılandırması göz atma nesnesi eklenir. Bu proje yapılandırması göz atma nesnesi Otomasyon Genişleticileri destekler. AutomationExtenders hakkında daha fazla bilgi için [bkz. Otomasyon Genişleticilerini Uygulama ve Kullanma.](/previous-versions/0y92k2w2(v=vs.140)) Temel projenin yapılandırma göz atma nesnesini genişleten kendi proje alt türü yapılandırma göz atma nesnesini almak için proje alt türü çağrısı tarafından <xref:EnvDTE.Project.Extender%2A> uygulanan özellik sayfaları.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:EnvDTE.IFilterProperties>
- [Özellik Sayfaları İletişim Kutusu](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))