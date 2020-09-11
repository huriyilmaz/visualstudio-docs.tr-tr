---
title: Proje özelliği kullanıcı arabirimi | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f15895a7dab5c57d8312787b1276acac89c28796
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011859"
---
# <a name="project-property-user-interface"></a>Proje Özelliği Kullanıcı Arabirimi

Proje alt türü, proje **Özellik sayfaları** iletişim kutusundaki öğeleri temel proje tarafından sağlandıklarında kullanabilir, salt okuma denetimlerini ve tüm sayfaları gizler veya belirtilen şekilde **Özellik sayfaları** iletişim kutusuna ekler.

## <a name="extending-the-project-property-dialog-box"></a>Proje özelliği Iletişim kutusunu genişletme

Proje alt türü Otomasyon Genişleticilerini ve proje yapılandırma nesneleri 'ni uygular. Bu Extender 'lar, <xref:EnvDTE.IFilterProperties> belirli özellikleri gizli veya salt okunurdur hale getirmek için arabirimini uygular. Temel proje tarafından uygulanan temel projenin **Özellik sayfaları** iletişim kutusu, Otomasyon Genişleticileri tarafından gerçekleştirilen filtrelemeyi geliştirir.

**Proje özelliği** iletişim kutusunu genişletme işlemi aşağıda özetlenmiştir:

- Temel proje, arabirimini uygulayarak proje alt türünden Extender 'lar alır <xref:EnvDTE80.IInternalExtenderProvider> . Bu arabirimi Uygula ' ya kadar, Proje Otomasyonu ve temel projenin proje yapılandırma nesnelerine Gözat edin.

- Proje için uygulama <xref:EnvDTE80.IInternalExtenderProvider> ve Proje Otomasyonu nesne temsilcisi, <xref:EnvDTE80.IInternalExtenderProvider> Proje alt türü toplayıcısı (yani, `QueryInterface` <xref:EnvDTE80.IInternalExtenderProvider> Proje nesnesi üzerinde için) uygulamasına Gözatılacak <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .

- Temel proje yapılandırması gezinme nesnesi Ayrıca, <xref:EnvDTE80.IInternalExtenderProvider> Proje alt türü yapılandırma nesnesinden Otomasyon genişleticisini doğrudan bağlamak için de uygular. Uygulama, <xref:EnvDTE80.IInternalExtenderProvider> Proje alt türü toplayıcısı tarafından uygulanan arabirime temsilciler.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>Proje yapılandırması nesnesine göre uygulanan nesnesi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nesnesini döndürür.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>Ayrıca, proje yapılandırması nesnesi tarafından uygulanan <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> nesne, nesnesini döndürür.

- Proje alt türü, aşağıdaki değerleri alarak, çalışma zamanında temel projenin farklı Genişletilebilir nesnelerinin uygun kasalarını belirleyebilir <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> :

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Proje kapsamı için CATIDs 'yi belirlemekte, proje alt türü [Vsitemıd için yukarıdaki özellikleri alır. Kaynağından kök](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) `VSITEMID typedef` . Proje alt türü Ayrıca, yapılandırma bağımlı ve yapılandırmaya bağımsız olarak proje için hangi **Özellik sayfaları** iletişim kutusu sayfalarının görüntülendiğini denetlemek isteyebilir. Bazı proje alt türleri, yerleşik sayfaları kaldırmak ve Project Subtype 'a özgü sayfaları eklemek zorunda kalabilir. Bunu etkinleştirmek için, yönetilen istemci projesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> aşağıdaki özellikler için yöntemini çağırır:

- `VSHPROPID_PropertyPagesCLSIDList` — yapılandırma bağımsız özellik sayfalarının CLSID 'leri için noktalı virgülle ayrılmış bir liste.

- `VSHPROPID_CfgPropertyPagesCLSIDList —` yapılandırmaya bağlı özellik sayfalarının CLSID 'lerin noktalı virgülle ayrılmış listesi.

Proje alt türü nesneyi topladığından <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , hangi **Özellik sayfaları** iletişim kutularının görüntülendiğini denetlemek için bu özelliklerin tanımını geçersiz kılabilir. Proje alt türü, bu özellikleri iç temel projeden alabilir ve ardından gerekirse CLSID 'leri ekleyebilir veya kaldırabilir.

Bir proje alt türü tarafından eklenen yeni özellik sayfaları, temel proje uygulamasından bir proje yapılandırması nesnesine sahiptir. Bu proje yapılandırma nesnesi Otomasyon Genişleticilerini destekler. Automationextender 'Lar hakkında daha fazla bilgi için bkz. [Otomasyon Genişleticilerini uygulama ve kullanma](/previous-versions/0y92k2w2(v=vs.140)). Proje alt türü tarafından uygulanan Özellik sayfaları, <xref:EnvDTE.Project.Extender%2A> temel projenin yapılandırma Gözat nesnesini genişleten kendi proje alt tür yapılandırması nesnesine gözatabiliyor.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:EnvDTE.IFilterProperties>
- [Özellik sayfaları Iletişim kutusu](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))