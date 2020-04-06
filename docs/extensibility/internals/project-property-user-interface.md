---
title: Proje Özelliği Kullanıcı Arabirimi | Microsoft Dokümanlar
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
ms.openlocfilehash: 4634eb5edaab16752bc5df82d70371a580845d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706393"
---
# <a name="project-property-user-interface"></a>Proje Özelliği Kullanıcı Arabirimi

Proje alt türü, temel proje tarafından sağlanan proje **Özellik Sayfaları** iletişim kutusundaki öğeleri kullanabilir, yalnızca okunan denetimleri ve tüm sayfaları sağlanan olarak gizleyebilir veya yapabilir veya **Özellik Sayfaları** iletişim kutusuna proje alt türüne özgü sayfalar ekleyebilir.

## <a name="extending-the-project-property-dialog-box"></a>Proje Özelliği İletişim Kutusunu Genişletme

Proje alt türü otomasyon genişleticiler ve proje yapılandırma sıcağa göz atar. Bu genişleticiler, belirli özellikleri gizli veya salt okunur hale getirmek için <xref:EnvDTE.IFilterProperties> arabirimi uygular. Temel proje tarafından uygulanan temel projenin **Özellik Sayfaları** iletişim kutusu, Otomasyon Genişleticiler tarafından gerçekleştirilen filtreleme onurlandırır.

**Project Property** iletişim kutusunu genişletme işlemi aşağıda özetlenmiştir:

- Temel proje <xref:EnvDTE80.IInternalExtenderProvider> arabirimi uygulayarak proje alt türünden genişleticiler alır. Göz atma, proje otomasyonu ve proje yapılandırması temel projenin nesnelerine göz atın, tüm bu arabirimi uygular.

- Proje <xref:EnvDTE80.IInternalExtenderProvider> için uygulama göz nesnesi ve proje otomasyonnesnesi proje alt türü toplayıcı <xref:EnvDTE80.IInternalExtenderProvider> (yani, `QueryInterface` <xref:EnvDTE80.IInternalExtenderProvider> onlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> proje nesnesi için) uygulanmasına temsilci.

- Temel proje yapılandırma göz atma <xref:EnvDTE80.IInternalExtenderProvider> nesnesi, proje alt türü yapılandırma nesnesinden Otomasyon Genişletici'ye doğrudan kablo yla da uygulanır. Uygulama, proje alt <xref:EnvDTE80.IInternalExtenderProvider> türü toplayıcısı tarafından uygulanan arabirimeye delege olur.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, proje yapılandırması tarafından uygulanan nesnegöz <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> at, nesne döndürür.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, ayrıca proje yapılandırması tarafından uygulanan nesne <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> göz atın, nesne döndürür.

- Proje alt türü, aşağıdaki <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> değerleri alarak, temel projenin çeşitli genişletilebilir nesneleri için uygun KATID'leri çalışma zamanında belirleyebilir:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Proje kapsamı için CATID'leri belirlemek için, proje alt türü VSITEMID için yukarıdaki özellikleri [alır. Kökten.](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) `VSITEMID typedef` Proje alt türü, proje için hem yapılandırmaya bağımlı hem de yapılandırmadan bağımsız olarak hangi **Özellik Sayfaları** iletişim kutusu sayfalarının görüntüleneceğini denetlemek de isteyebilir. Bazı proje alt türlerinin yerleşik sayfaları kaldırması ve proje alt türüne belirli sayfalar eklemesi gerekebilir. Bunu etkinleştirmek için yönetilen istemci projesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> aşağıdaki özellikler için yöntemi çağırır:

- `VSHPROPID_PropertyPagesCLSIDList`— yapılandırmadan bağımsız özellik sayfalarının CLSID'lerinin yarı kolonlu sınırlı bir listesi.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`yapılandırmaya bağımlı özellik sayfalarının CLSID'lerinin yarı sütunlu sınırlı bir listesi.

Proje alt türü nesneyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> alabildiği için, hangi **Özellik Sayfaları** iletişim kutularının görüntüleneceğini denetlemek için bu özelliklerin tanımını geçersiz kılabilir. Proje alt türü bu özellikleri iç temel projeden alabilir ve gerektiğinde CLSID'leri ekleyebilir veya kaldırabilir.

Proje alt türü tarafından eklenen yeni özellik sayfaları, temel proje uygulamasından proje yapılandırması tarama nesnesi verilir. Bu proje yapılandırması tarama nesnesi Otomasyon Genişleticiler destekler. AutomationExtenders hakkında daha fazla bilgi için [bkz.](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356) Proje alt türü tarafından uygulanan özellik <xref:EnvDTE.Project.Extender%2A> sayfaları, temel projenin yapılandırma tarama nesnesini genişleten kendi proje alt türü yapılandırmasını almak için çağrı da.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:EnvDTE.IFilterProperties>
- [Özellik Sayfaları İletişim Kutusu](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
