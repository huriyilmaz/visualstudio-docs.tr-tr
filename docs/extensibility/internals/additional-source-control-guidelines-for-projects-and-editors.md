---
title: Projeler ve düzenleyiciler için kaynak denetimi yönergeleri
description: Kaynak denetimine destek olmak için projelerin ve düzenleyicilerin uyması gereken yönergeler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 68934fb67ff1bd4f17507ac4af72c0aaf113816c6b6ff643c9f49bbb40698e81
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414694"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Projeler ve düzenleyiciler için ek kaynak denetimi yönergeleri
Projelerin ve düzenleyicilerin kaynak denetimi desteklemek için uyması gereken bir dizi kılavuz vardır.

## <a name="guidelines"></a>Yönergeler
 Projeniz veya düzenleyiciniz kaynak denetimi desteklemek için şunları da gerçekleştirmalıdır:

|Alan|Project|Düzenleyici|Ayrıntılar|
|----------|-------------|------------|-------------|
|Dosyaların özel kopyaları|X||Ortam, dosyaların özel kopyalarını destekler. Başka bir ifadeyle, projede yer alan her bir kişinin, bu projede yer alan dosyaların kendi özel kopyası vardır.|
|ANSI/Unicode kalıcılığı|X|X|Kalıcılık kodunu yazarsanız, çoğu kaynak denetim programı şu anda Unicode'u desteklemey olduğundan, dosyaları ANSI formunda kalıcı olarak kalıcı olarak bulundurabilirsiniz.|
|Dosyaları numarala|X||Proje, içindeki tüm dosyaların belirli bir listesini içermeli ve veya (VSH_PROPID_First_Child/Next_Sibling) kullanarak dosya <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> listesini listeleye VSH_PROPID_First_Child. Proje ayrıca uygulama aracılığıyla öğe adlarını ve uygulama aracılığıyla <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> ad aramasını (özel dosyalar dahil) desteklemesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> gerekir.|
|Metin biçimi|X|X|Mümkün olduğunda, farklı sürümlerin birleştirilmesini desteklemek için dosyalar metin biçiminde olmalıdır. Metin biçiminde yer alan dosyalar daha sonra dosyanın diğer sürümleriyle birleştirilemez. Tercih edilen metin biçimi XML'tir.|
|Başvuru tabanlı|X||Başvuru tabanlı projeler, kaynak denetiminde hazır olarak de desteklene. Ancak, proje, dosyaların diskte mevcut olup olmadığı bağımsız olarak isteğe bağlı olarak dosyalarının bir listesini üretebilir sürece, dizin tabanlı projeler kaynak denetimi tarafından da de desteklemektedir. Bir projeyi kaynak denetiminden a açılışında, proje dosyası herhangi bir dosyadan önce ilk olarak aşağı indirildi.|
|Nesneleri ve özellikleri öngörülebilir sırada kalıcı hale|X|X|Birleştirmeyi kolaylaştırmak için dosyalarınızı alfabetik sıra gibi öngörülebilir bir sırada kalıcı hale.|
|Yeniden yükle|X|X|Diskte bir dosya değişirse, düzenleyiciniz dosyayı yeniden yükleyene kadar devam etmek zorunda olur. Kaynak denetimine katılarak ortamınız, uygulamanızı çağırarak sizin için verileri yeniden <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> yükler. En zor yeniden yükleme durumu, IVsQueryEditQuerySave:: çağrısında ve bilgi işleme sırasında bir iade <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> işleminin gerçekleşmesidir. Ancak, yeniden yükleme kodunuzun bu durumda çalıştırıla çalışması gerekir.<br /><br /> Ortam proje dosyalarını otomatik olarak yeniden yüklenir. Ancak, bir projenin, iç içe geçmiş proje dosyalarının yeniden yüklemesini desteklemek için iç içe geçmiş hiyerarşileri varsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> uygulaması gerekir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi desteği](../../extensibility/internals/supporting-source-control.md)
