---
title: Sorgu Yı Küçülme (Kaynak Denetimi VSPackage) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c09ac0cb4f51b8f2484b95d403ff6d0445631479
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705966"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Sorgu Düzenleme Sorgu Kaydetme (Kaynak Denetimi VSPackage’ı)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]düzenleyiciler Sorgu Edit Sorgu Kaydet (QEQS) olaylarını yayınlayabilirler. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kaynak Denetim Saplaması QEQS hizmetini uygular, böylece QEQS olaylarının alıcısı olur. Bu olaylar daha sonra şu anda etkin olan kaynak denetimi VSPackage'a devredilir. Aktif kaynak kontrolü VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> ve yöntemlerini uygular. `IVsQueryEditQuerySave2` Arabirimin yöntemleri genellikle belge ilk kez düzenlenmeden hemen önce ve belge kaydedilmeden hemen önce çağrılır.

## <a name="queryeditquerysave-events"></a>QueryEditQueryOlayları Kaydet
 Kaynak denetimi VSPackage `IVsQueryEditQuerySave2` arabirimi ve gerekli yöntemleri uygulayarak QEQS olaylarını ele almalıdır. Aşağıda VSPackage en az uygulanması gereken iki yöntemin kısa bir açıklaması dır. Gerçek uygulama kaynak denetim modelinin mantığına uygun olmalıdır.

### <a name="queryeditfiles-method"></a>Sorgulanan Dosyalar Yöntemi
 Herhangi <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> bir proje veya düzenleyici bir dosyayı değiştirmek istediğinde çağrılır. İdeal olarak, bu yöntem dosya değiştirilmeden *ve* bir dosya kaydedildiğinde çağrılır. Çağrıldığında, `IVsQueryEditQuerySave2::QueryEditFiles` yöntem verilen dosyaların kaynak denetimi altında olup olmadığını, kullanıma alınması gerekip gerekmediğini ve yeniden yüklenip yüklenemeyeceğini denetler. Koşullar dosyaların edinilebilir olmasını engelliyorsa, `IVsQueryEditQuerySave2::QueryEditFiles` yöntem arama programına aramayı iptal etmesini söyler. Arayanın bir çağırma modu belirtebetmesi de mümkündür. "Sessiz" modunda, bu yöntem yalnızca herhangi bir UI'nin görünmesine neden olmadığı durumlarda işlem yapar. UI kaçınılmazsa, sorunu belirtmek için bir bayrak döndürülmelidir.

 Yöntem işlemsel bir şekilde çalışır; diğer bir yerde, tek bir dosyada yapılan edit iptal edilirse, tüm dosyalar için yapılan edit iptal edilir. Tersine, edite izin verilirse, tüm dosyalar için izin verilir. Bu yöntem belirli bir dosya kümesi için bir kez düzenlemeye izin veriyorsa, aynı dosya kümesi için sonraki çağrılarda her zaman düzenleme yapılmasına izin vermelidir. İzin verme döngüsü, dosyalar kapatılıp kaydedilene ve yeniden yüklenene kadar devam ediyor; öznitelikleri (özellikleri) değişene kadar; veya kaynak kontrol paketi değiştirilene kadar. Yöntemin `IVsQueryEditQuerySave2::QueryEditFiles` uygulanmasında göz önünde bulundurulması gereken durumlar arasında birden çok dosya, özel dosya, kullanıcıdan iptal etme ve bellek içi de

### <a name="querysavefiles-method"></a>QuerySaveFiles Yöntemi
 Herhangi <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> bir proje veya düzenleyici bir dosya kümesi kaydetmek gerektiğinde çağrılır. Çağrıldığında, `IVsQueryEditQuerySave2::QuerySaveFiles` yöntem verilen dosyaların salt okunur olup olmadığını ve kaynak denetimi altında olup olmadığını denetler. Dosyaların kullanıma alınması gerekiyorsa, arama kaynak denetim paketine devredilir. Koşullar dosyaların kaydolmasını engelliyorsa, `IVsQueryEditQuerySave2::QuerySaveFiles` yöntemin düzenleyiciye kaydediyi iptal etmesini söylemesi gerekir. `IVsQueryEditQuerySave2::QueryEditFiles` Yöntemde olduğu gibi, arayanın bir çağırma modu belirtebetmesi mümkündür. "Sessiz" modunda, bu yöntem yalnızca herhangi bir UI'nin görünmesine neden olmadığı durumlarda işlem yapar. UI kaçınılmazsa, sorunu belirtmek için bir bayrak döndürülmelidir.

 Bu yöntem işlemsel bir şekilde hareket etmelidir; diğer bir de, kaydetme tek bir dosyada iptal edilirse, tüm dosyalar için kaydetme iptal edilir. Tersine, kayda izin verilirse, tüm dosyalar için izin verilmelidir. `IVsQueryEditQuerySave2::QueryEditFiles` Yöntemde olduğu gibi, `IVsQueryEditQuerySave2::QuerySaveFiles` yöntemin uygulanmasında göz önünde bulundurulması gereken durumlar arasında birden çok dosya, özel dosya, kullanıcıdan iptal etme ve bellek içi deekler yer alır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
