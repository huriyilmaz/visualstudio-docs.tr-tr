---
title: Sorgu düzenleme sorgu kaydetme (kaynak denetimi VSPackage) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ad0cf7c3e1d3269dbe7ebee051cc32e2e8531ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148898"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Sorgu Düzenleme Sorgu Kaydetme (Kaynak Denetimi VSPackage’ı)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] düzenleyiciler, sorgu düzenleme sorgusu kaydetme (QEQS) olaylarını yayınlayabilir. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Kaynak denetimi saplaması QEQS hizmetini uygular, bu sayede QEQS olaylarının alıcısı olur. Bu olaylar daha sonra şu anda etkin kaynak denetimi VSPackage için temsilci olarak atanır. Etkin kaynak denetimi VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> ve yöntemlerini uygular. `IVsQueryEditQuerySave2`Arabirim yöntemleri genellikle bir belge ilk kez düzenlendikten hemen önce ve bir belge kaydedilmeden hemen önce çağrılır.  
  
## <a name="queryeditquerysave-events"></a>QueryEditQuerySave olayları  
 Kaynak denetimi VSPackage, arabirimi ve gerekli yöntemleri uygulayarak QEQS olaylarını işlemelidir `IVsQueryEditQuerySave2` . Aşağıda, VSPackage 'ın en az bir olarak uygulanması gereken iki yöntemin kısa bir açıklaması verilmiştir. Gerçek uygulamanın, kaynak denetimi modelinin mantığına uygun olması gerekir.  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles yöntemi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>Herhangi bir proje ya da düzenleyici bir dosyayı değiştirmek istediğinde çağrılır. İdeal olarak, bu yöntem dosya değiştirilmeden *önce* ve bir dosya kaydedildiğinde çağırılır. Çağrıldığında, `IVsQueryEditQuerySave2::QueryEditFiles` Yöntemi verilen dosyaların kaynak denetimi altında olup olmadığını, kullanıma alınması gerekip gerekmediğini ve yeniden yüklenip yüklenmediğini denetler. Koşullar dosyaların düzenlenebilmesini engelliyorsa, `IVsQueryEditQuerySave2::QueryEditFiles` yöntemi çağıran programa düzenlemeyi iptal edip etmeyeceğini söyler. Çağıranın bir çağırma modu belirtmesi de mümkündür. "Sessiz" modda, bu yöntem yalnızca herhangi bir UI 'nin görünmesine neden değilse işlem yapar. Kullanıcı arabirimine kaçınılmaz ise, sorunu belirtmek için bir bayrak döndürülmelidir.  
  
 Yöntemi işlem halinde davranır; diğer bir deyişle, düzenleme tek bir dosyada iptal edilirse, tüm dosyalar için düzenleme iptal edilir. Buna karşılık, düzenlemeye izin veriliyorsa tüm dosyalar için izin verilir. Bu yöntem, belirli bir dosya kümesi için bir kez düzenlenmesine izin veriyorsa, aynı dosya kümesi için sonraki çağrıların düzenlenmesine her zaman izin vermelidir. İzin ver-Düzenle döngüsü, dosyalar kapatılana, kaydedilene ve yeniden yüklenene kadar devam eder; öznitelikleri (Özellikler) değişene kadar; kaynak denetim paketi değiştirilene kadar. Yöntemi uygularken dikkate alınması gereken durumlar `IVsQueryEditQuerySave2::QueryEditFiles` arasında birden çok dosya, özel dosya, Kullanıcı iptali ve bellek içi düzenlemeler sayılabilir.  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles yöntemi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>Herhangi bir proje ya da düzenleyicinin bir dosya kümesini kaydetmesi gerektiğinde çağrılır. Çağrıldığında, `IVsQueryEditQuerySave2::QuerySaveFiles` Yöntemi verilen dosyaların salt okunurdur ve kaynak denetimi altında olup olmadığını denetler. Dosyaların kullanıma alınması gerekiyorsa, çağrı kaynak denetim paketi için temsilci olarak oluşturulur. Koşullar dosyaların kaydedilmesini engelliyorsa, `IVsQueryEditQuerySave2::QuerySaveFiles` yöntemi düzenleyiciye, kaydetme işlemini iptal etmek için söylemelidir. Yönteminde olduğu gibi `IVsQueryEditQuerySave2::QueryEditFiles` , çağıranın bir çağırma modu belirtmesi mümkündür. "Sessiz" modda, bu yöntem yalnızca herhangi bir UI 'nin görünmesine neden değilse işlem yapar. Kullanıcı arabirimine kaçınılmaz ise, sorunu belirtmek için bir bayrak döndürülmelidir.  
  
 Bu yöntem işlemsel bir şekilde davranmalıdır; diğer bir deyişle, tek bir dosyada kaydet iptal edilirse, tüm dosyalar için kaydetme iptal edilir. Buna karşılık, kaydetmeye izin veriliyorsa tüm dosyalar için izin verilmelidir. Yönteminde olduğu gibi `IVsQueryEditQuerySave2::QueryEditFiles` , yöntemini uygulamak için göz önünde bulundurmanız gereken durumlar `IVsQueryEditQuerySave2::QuerySaveFiles` arasında birden çok dosya, özel dosya, Kullanıcı iptali ve bellek içi düzenlemeler sayılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
