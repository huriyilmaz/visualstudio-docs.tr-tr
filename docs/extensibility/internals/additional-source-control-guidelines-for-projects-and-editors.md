---
title: Projeler ve Editörler için Ek Kaynak Kontrol Yönergeleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 181f6c10ff7ce95cd3a37151f117353d1bb47d41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710118"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Projeler ve editörler için ek kaynak denetimi yönergeleri
Kaynak denetimini desteklemek için projelerin ve editörlerin uyması gereken bir dizi yönerge vardır.

## <a name="guidelines"></a>Yönergeler
 Projeniz veya düzenleyiciniz kaynak denetimini desteklemek için aşağıdakileri de yapmalıdır:

|Alan|Project|Düzenleyici|Ayrıntılar|
|----------|-------------|------------|-------------|
|Dosyaların özel kopyaları|X||Ortam, dosyaların özel kopyalarını destekler. Diğer bir deyişle, projeye kaydolan her kişinin, projedeki dosyaların kendi özel kopyası vardır.|
|ANSI/Unicode kalıcılığı|X|X|Kalıcılık kodunu yazarsanız, çoğu kaynak denetim programı şu anda Unicode'u desteklemediği için dosyaları ANSI formunda devam edin.|
|Dosyaları sayısallandırma|X||Proje, içindeki tüm dosyaların belirli bir listesini içermelidir ve (VSH_PROPID_First_Child/Next_Sibling) kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> dosyaların listesini sayısala değnebilmelidir. Proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> ayrıca, uygulama yoluyla madde adlarını ortaya çıkarmalı ve uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> yoluyla ad aramasını (özel dosyalar dahil) desteklemelidir.|
|Metin biçimi|X|X|Mümkün olduğunda, dosyaların farklı sürümlerin birleştirilmesini desteklemek için metin biçiminde olması gerekir. Metin biçiminde olmayan dosyalar daha sonra dosyanın diğer sürümleriyle birleştirilemez. Tercih edilen metin biçimi XML'dir.|
|Referans tabanlı|X||Referans tabanlı projeler kaynak denetiminde kolayca desteklenir. Ancak, dizin tabanlı projeler, bu dosyaların diskte bulunup bulunmadığına bakılmaksızın, proje talep üzerine dosyalarının bir listesini oluşturabildiği sürece kaynak denetimi tarafından da desteklenir. Bir projeyi kaynak denetiminden açarken, proje dosyası önce dosyalarından önce aşağı indirilir.|
|Nesneleri ve özellikleri öngörülebilir sırada kalıcı hale|X|X|Birleştirmeyi kolaylaştırmak için dosyalarınızı alfabetik sıra gibi öngörülebilir bir sırada devam edin.|
|Yeniden yükle|X|X|Bir dosya diskte değiştiğinde, düzenleyiciniz dosyayı yeniden yükleyebilmeli. Kaynak denetimine katıldığınızda, ortam uygulamanızı <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> arayarak verileri sizin için yeniden yükler. En zor yeniden yükleme durumu, IVsQueryEditQuerySave::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ve bilgileri işleyen bir ödeme oluşur. Ancak, yeniden yükleme kodunuz bu durumda çalıştırılabilmelidir.<br /><br /> Ortam proje dosyalarını otomatik olarak yeniden yükler. Ancak, iç içe <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> olan proje dosyalarını yeniden yüklemek için bir proje iç içe hiyerarşileri varsa uygulaması gerekir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Destek kaynak denetimi](../../extensibility/internals/supporting-source-control.md)
