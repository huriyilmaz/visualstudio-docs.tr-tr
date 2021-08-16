---
title: Belge Tablosu Çalıştırma | Microsoft Docs
description: IDE'Visual Studio açık tüm belgeleri içeren çalışan belge tablosu nasıl korunur?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5ef96a878c11b51a99a501b448362a8ee0146c3815d94a32b9e4ef5893b545f6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401225"
---
# <a name="running-document-table"></a>Çalıştırılan Belge Tablosu
IDE, şu anda açık olan tüm belgelerin listesini, çalışan belge tablosu (RDT) adlı bir iç yapıda bulundurarak sürdürür. Bu liste, şu anda düzende olup olmadığına bakılmaksızın bellekte açık olan tüm belgeleri içerir. Belge, bir proje veya ana proje dosyası (örneğin, .vcxproj dosyası) dahil olmak üzere kalıcı olan herhangi bir öğedir.

## <a name="elements-of-the-running-document-table"></a>Çalışan Belge Tablosu Öğeleri
 Çalışan belge tablosu aşağıdaki girişleri içerir.

|Öğe|Açıklama|
|-------------|-----------------|
|Belge bilinen adı|Belge veri nesnesini benzersiz olarak tanımlayan bir dize. Bu, dosyaları yöneten bir proje sisteminin mutlak dosya yoludur (örneğin, C:\MyProject\MyFile). Bu dize, bir veritabanındaki saklı yordamlar gibi dosya sistemleri dışında depolara kaydedilen projeler için de kullanılır. Bu durumda proje sistemi, belgeyi nasıl depolaydığını belirlemek için tanıyarak ve ayrıştırarak benzersiz bir dizeyi ortaya ekleyebilirsiniz.|
|Hiyerarşi sahibi|Bir arabirimle temsil edilen belgeye sahip hiyerarşi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nesnesi.|
|Öğe Kimliği|Hiyerarşi içindeki belirli bir öğenin öğe tanımlayıcısı. Bu değer, hiyerarşide bu belgeye sahip olan tüm belgeler arasında benzersizdir, ancak bu değerin farklı hiyerarşilerde benzersiz olması garanti edilemez.|
|Belge veri nesnesi|En azından bu bir `IUnknown`<br /><br /> Nesne. IDE, özel düzenleyicinin belge veri nesnesi `IUnknown` için arabirimin ötesinde belirli bir arabirim gerektirmez. Ancak standart bir düzenleyicide, projeden gelen dosya kalıcılık çağrılarını işlemek için düzenleyicinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> arabirimi uygulaması gerekir. Daha fazla bilgi için [bkz. Standart Belge kaydetme.](../../extensibility/internals/saving-a-standard-document.md)|
|Bayraklar|Belgenin kaydedip kaydedil olmadığını, okuma veya düzenleme kilidi uygulanıp uygulanmadığını ve bu şekilde devam etmek için RDT'ye girişler ekleniyorsa bayraklar belirtilebilir. Daha fazla bilgi için <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> bkz. numaralama.|
|Kilit Sayısını Düzenle|Düzenleme kilitlerinin sayısı. Düzenleme kilidi, bazı düzenleyicilerde belgenin düzenleme için açık olduğunu gösterir. Düzenleme kilitlerinin sayısı sıfıra geçildiğinde, değiştirilmişse kullanıcıdan belgeyi kaydetmesi istenir. Örneğin, Yeni Pencere komutunu kullanarak bir belgeyi düzenleyicide her açsanız RDT'de bu belge için bir düzenleme kilidi eklenir.  Düzenleme kilidinin ayarlan için belgenin hiyerarşisi veya öğe kimliği olmalıdır.|
|Okuma Kilidi Sayısı|Okuma kilitlerinin sayısı. Okuma kilidi, belgenin sihirbaz gibi bir mekanizma aracılığıyla okunmakta olduğunu gösterir. Okuma kilidi, belgeyi RDT'de canlı tutarken belgenin düzenlenemez olduğunu gösterir. Belgede hiyerarşi veya öğe kimliği yoksa bile okuma kilidi ayarlayın. Bu özellik, bir belgeyi bellekte açıp herhangi bir hiyerarşiye ait olmadan RDT'ye girmenize olanak sağlar. Bu özellik nadiren kullanılır.|
|Kilit tutucu|Arabirimin <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> örneği. Kilit tutucu, belgeleri düzenleyici dışında açıp düzenleyen sihirbazlar gibi özellikler tarafından uygulanır. Kilit tutucu, özelliğin belge hala düzenlenmişken belgenin kapatılamaması için belgeye düzenleme kilidi eklemesini sağlar. Normalde, düzenleme kilitleri yalnızca belge pencereleri (düzenleyiciler) tarafından eklenir.|

 RDT'deki her giriş, genellikle projedeki bir düğüme karşılık gelen benzersiz bir hiyerarşiye veya öğe kimliğine sahip. Düzenleme için kullanılabilen tüm belgeler genellikle bir hiyerarşiye aittir. RDT denetiminde yapılan girişler, şu anda düzenmakta olan belge veri nesnesinin sahibi olan proje veya daha doğru olan hiyerarşidir. IDE, RDT'de bilgileri kullanarak bir belgenin aynı anda birden fazla proje tarafından açılmasını önlenebilir.

 Hiyerarşi ayrıca verilerin kalıcılıklarını da kontrol eder ve RDT'de kaydet ve Farklı Kaydet **iletişim** **kutularını güncelleştirmek için** bilgileri kullanır. Kullanıcılar bir belgeyi değiştirdiğinde  ve ardından  Dosya menüsünden Çıkış komutunu seçtiklerinde, IDE onlara Değişiklikleri Kaydet iletişim kutusunu kullanarak o anda değiştirilmiş olan tüm projeleri ve proje öğelerini gösterir.  Bu, kullanıcıların hangi belgelerin kaydedeceklerini seçmelerini sağlar. Kaydedecek belgelerin listesi (yani, değişiklikleri olan belgeler) RDT'den oluşturulur. Uygulamadan çıkarken Değişiklikleri Kaydet  iletişim kutusunda görmeyi beklediğiniz tüm öğelerin RDT'de kayıtları olması gerekir. RDT, hangi belgelerin kaydediliyor ve her belge için Flags girdisinde belirtilen değerleri kullanarak kullanıcıdan bir kaydetme işlemi olup olmadığını koordine eder. RDT bayrakları hakkında daha fazla bilgi için <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> bkz. numaralama.

## <a name="edit-locks-and-read-locks"></a>Kilitleri Ve Okuma Kilitlerini Düzenleme
 Düzenleme kilitleri ve okuma kilitleri RDT'de yer alan. Belge penceresi düzenleme kilidini artırır ve geriler. Bu nedenle, kullanıcı yeni bir belge penceresi açtığında, düzenleme kilidi sayısı bir artarak. Düzenleme kilitlerinin sayısı sıfıra ulaştığında, hiyerarşiye ilişkili belge için verileri kalıcı olarak kaydetmesi veya kaydetmesi işaretlenir. Daha sonra hiyerarşi, verileri herhangi bir şekilde kalıcı olarak (dosya olarak veya depoda bir öğe olarak kalıcı olarak) bulundurabilirsiniz. Düzenleme kilitleri ve okuma kilitleri eklemek için arabiriminde yöntemini ve bu kilitleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> kaldırma yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> kullanabilirsiniz.

 Normalde, bir düzenleyicinin belge penceresi örneği ekleyebilirsiniz, pencere çerçevesi RDT'de belge için otomatik olarak bir düzenleme kilidi ekler. Ancak, standart bir belge penceresi kullanmayan bir belgenin özel bir görünümünü (yani arabirimi uygulamaz) ekleyebilirsiniz, ardından kendi düzenleme <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> kilidinizi ayarlamanız gerekir. Örneğin sihirbazda bir belge, düzenleyicide açık olmadan düzenlenmiştir. Belge kilitlerinin sihirbazlar ve benzer varlıklar tarafından açılması için bu varlıkların arabirimini uygulaması <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> gerekir. Belge kilit tutucusuz kaydetmek için yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> çağırarak uygulamanıza <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> geçişin. Bunu yapmak, belge kilit tutucus nizi RDT'ye ekler. Bir belge kilit tutucusunu uygulamaya başka bir senaryo da, bir belgeyi özel bir araç penceresi aracılığıyla açmadır. Bu örnekte, araç penceresinin belgeyi kapatması mümkün değildir. Ancak, RDT'de belge kilit tutucusu olarak kaydederek IDE, belgeyi kapatmak için yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> uygulamanızı çağırabilirsiniz.

## <a name="other-uses-of-the-running-document-table"></a>Çalışan Belge Tablosu'nın Diğer Kullanımları
 IDE'de diğer varlıklar, belgeler hakkında bilgi almak için RDT'yi kullanır. Örneğin, kaynak denetim yöneticisi RDT'yi kullanır ve dosyanın en yeni sürümünü edindikten sonra sisteme düzenleyicide bir belgeyi yeniden yüklemelerini söyler. Bunu yapmak için, kaynak denetim yöneticisi RDT'de herhangi bir dosyanın açık olup o dosyalarına bakamaz. Varsa, kaynak denetim yöneticisi önce hiyerarşinin yöntemini uygulaydığını görmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> denetler. Proje yöntemini uygulamazsa, kaynak denetim yöneticisi doğrudan belge veri <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> nesnesinde yönteminin uygulanmasını denetler.

 IDE ayrıca, bir kullanıcı belgeyi talep ediyorsa açık bir belgeyi yeniden açmak (öne getir) için RDT kullanır. Daha fazla bilgi için [bkz. Dosya Aç Komutunu Kullanarak Dosyaları Görüntüleme.](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md) RDT'de bir dosyanın açık olup olmadığını belirlemek için aşağıdakini yapın.

- Öğenin açık olup olduğunu bulmak için belge bilinen adı (yani tam belge yolu) için sorgu oluşturun.

- Proje sisteminde tam belge yolunu istemek için hiyerarşiyi veya öğe kimliğini kullanın ve rdt'de öğeyi arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [RDT_ReadLock Kullanımı](../../extensibility/internals/rdt-readlock-usage.md)
- [Kalıcılık ve Çalıştırılan Belge Tablosu](../../extensibility/internals/persistence-and-the-running-document-table.md)
