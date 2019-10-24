---
title: Sorgu düzenleme sorgu kaydetme (kaynak denetimi VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be12297bdaeb112d7421b02da1153ed62d6d14f8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724765"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Sorgu Düzenleme Sorgu Kaydetme (Kaynak Denetimi VSPackage’ı)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] düzenleyiciler, sorgu düzenleme sorgusu kaydetme (QEQS) olaylarını yayınlayabilir. Kaynak denetimi saplaması [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] QEQS hizmetini uygular, bu sayede QEQS olaylarının alıcısı olur. Bu olaylar daha sonra şu anda etkin kaynak denetimi VSPackage için temsilci olarak atanır. Etkin kaynak denetimi VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> ve yöntemlerini uygular. @No__t_0 arabiriminin yöntemleri, genellikle bir belge ilk kez düzenlenirken ve bir belge kaydedilmeden hemen önce çağrılır.

## <a name="queryeditquerysave-events"></a>QueryEditQuerySave olayları
 Kaynak denetimi VSPackage, `IVsQueryEditQuerySave2` arabirimini ve gerekli yöntemleri uygulayarak QEQS olaylarını işlemelidir. Aşağıda, VSPackage 'ın en az bir olarak uygulanması gereken iki yöntemin kısa bir açıklaması verilmiştir. Gerçek uygulamanın, kaynak denetimi modelinin mantığına uygun olması gerekir.

### <a name="queryeditfiles-method"></a>QueryEditFiles yöntemi
 @No__t_0, herhangi bir proje veya düzenleyici bir dosyayı değiştirmek istediğinde çağrılır. İdeal olarak, bu yöntem dosya değiştirilmeden *önce* ve bir dosya kaydedildiğinde çağırılır. Çağrıldığında `IVsQueryEditQuerySave2::QueryEditFiles` yöntemi, verilen dosyaların kaynak denetimi altında olup olmadığını, kullanıma alınması gerekip gerekmediğini ve yeniden yüklenip yüklenmeyeceğini denetler. Koşullar dosyaların düzenlenebilmesini engelliyorsa `IVsQueryEditQuerySave2::QueryEditFiles` yöntemi çağıran programa düzenlemeyi iptal edip etmeyeceğini söyler. Çağıranın bir çağırma modu belirtmesi de mümkündür. "Sessiz" modda, bu yöntem yalnızca herhangi bir UI 'nin görünmesine neden değilse işlem yapar. Kullanıcı arabirimine kaçınılmaz ise, sorunu belirtmek için bir bayrak döndürülmelidir.

 Yöntemi işlem halinde davranır; diğer bir deyişle, düzenleme tek bir dosyada iptal edilirse, tüm dosyalar için düzenleme iptal edilir. Buna karşılık, düzenlemeye izin veriliyorsa tüm dosyalar için izin verilir. Bu yöntem, belirli bir dosya kümesi için bir kez düzenlenmesine izin veriyorsa, aynı dosya kümesi için sonraki çağrıların düzenlenmesine her zaman izin vermelidir. İzin ver-Düzenle döngüsü, dosyalar kapatılana, kaydedilene ve yeniden yüklenene kadar devam eder; öznitelikleri (Özellikler) değişene kadar; kaynak denetim paketi değiştirilene kadar. @No__t_0 yöntemi uygularken dikkate alınması gereken durumlar, birden çok dosya, özel dosya, kullanıcının iptali ve bellek içi düzenlemelerde yer alır.

### <a name="querysavefiles-method"></a>QuerySaveFiles yöntemi
 @No__t_0, herhangi bir proje ya da düzenleyicinin bir dosya kümesini kaydetmesi gerektiğinde çağrılır. Çağrıldığında `IVsQueryEditQuerySave2::QuerySaveFiles` Yöntemi verilen dosyaların salt okunurdur ve kaynak denetimi altında olup olmadığını denetler. Dosyaların kullanıma alınması gerekiyorsa, çağrı kaynak denetim paketi için temsilci olarak oluşturulur. Koşullar dosyaların kaydedilmesini engelliyorsa `IVsQueryEditQuerySave2::QuerySaveFiles` yöntemi, düzenleyiciye kaydetme işlemini iptal etmek için düzenleyiciyi anlatmalıdır. @No__t_0 yönteminde olduğu gibi, çağıranın bir çağırma modu belirtmesi mümkündür. "Sessiz" modda, bu yöntem yalnızca herhangi bir UI 'nin görünmesine neden değilse işlem yapar. Kullanıcı arabirimine kaçınılmaz ise, sorunu belirtmek için bir bayrak döndürülmelidir.

 Bu yöntem işlemsel bir şekilde davranmalıdır; diğer bir deyişle, tek bir dosyada kaydet iptal edilirse, tüm dosyalar için kaydetme iptal edilir. Buna karşılık, kaydetmeye izin veriliyorsa tüm dosyalar için izin verilmelidir. @No__t_0 yönteminde olduğu gibi, `IVsQueryEditQuerySave2::QuerySaveFiles` metodunu uygularken dikkate alınması gereken durumlar, birden çok dosya, özel dosya, kullanıcıdan iptal etme ve bellek içi düzenlemelerde yer alır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>