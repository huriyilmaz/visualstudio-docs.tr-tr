---
title: Çalışma Belge Tablosu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e6aa882921786b1592922372581beae8c4c2443
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705562"
---
# <a name="running-document-table"></a>Çalıştırılan Belge Tablosu
IDE, çalışan belge tablosu (RDT) adı verilen bir iç yapıda şu anda açık olan tüm belgelerin listesini tutar. Bu liste, bu belgelerin şu anda düzenlenip düzenlenmediğine bakılmaksızın bellekteki tüm açık belgeleri içerir. Belge, projedeki veya ana proje dosyasındaki dosyalar (örneğin, .vcxproj dosyası) dahil olmak üzere kalıcı olan herhangi bir öğedir.

## <a name="elements-of-the-running-document-table"></a>Çalışan Belge Tablosunun Öğeleri
 Çalışan belge tablosu aşağıdaki girişleri içerir.

|Öğe|Açıklama|
|-------------|-----------------|
|Belge lakabı|Belge veri nesnesini benzersiz olarak tanımlayan bir dize. Bu, dosyaları yöneten bir proje sistemi için mutlak dosya yolu olacaktır (örneğin, C:\MyProject\MyFile). Bu dize, veritabanında depolanan yordamlar gibi dosya sistemleri dışındaki mağazalarda kaydedilen projeler için de kullanılır. Bu durumda, proje sistemi tanıyabilir ve büyük olasılıkla belgenin nasıl depolanır belirlemek için ayrıştırmak için benzersiz bir dize icat edebilirsiniz.|
|Hiyerarşi sahibi|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Arabirim tarafından temsil edildiği üzere belgenin sahibi olan hiyerarşi nesnesi.|
|Öğe Kimliği|Hiyerarşi içindeki belirli bir öğe için öğe tanımlayıcısı. Bu değer, bu belgenin sahibi olan hiyerarşideki tüm belgeler arasında benzersizdir, ancak bu değerin farklı hiyerarşiler arasında benzersiz olacağı garanti edilmez.|
|Belge veri nesnesi|En azından, bu bir`IUnknown`<br /><br /> Nesne. IDE, özel bir düzenleyicinin `IUnknown` belge veri nesnesi için arabirim dışında belirli bir arabirim gerektirmez. Ancak, standart bir düzenleyici için, düzenleyicinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> arabirimi uygulaması, projeden gelen dosya kalıcılığı çağrılarını işlemek için gereklidir. Daha fazla bilgi için [bkz.](../../extensibility/internals/saving-a-standard-document.md)|
|Bayraklar|Belgenin kaydedilip kaydedilmeyeceğini, okuma veya edit kilidi uygulanıp uygulanmadığını ve benzeri olmayan bayraklar, girişler RDT'ye eklendiğinde belirtilebilir. Daha fazla bilgi <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> için numaralandırmaya bakın.|
|Kilit Sayısını Edit|Ayarla kilitleri sayısı. Düzenleme kilidi, bazı düzenleyicinin belgeyi düzenleme için açık olduğunu gösterir. Düzenlendis sayısı sıfıra geçiş yaptığında, kullanıcıdan belgeyi kaydetmesi istenir. Örneğin, **Yeni Pencere** komutunu kullanarak bir düzenleyicide bir belgeyi her açtığınızda, RDT'deki bu belge için bir edit kilidi eklenir. Bir düzen kilidi ayarlanabilmesi için belgenin bir hiyerarşi veya öğe kimliği olması gerekir.|
|Kilit Sayısını Oku|Okuma kilitleri sayısı. Okuma kilidi, belgenin sihirbaz gibi bazı mekanizmalar aracılığıyla okunduğunu gösterir. Okuma kilidi, belgenin düzenlenemeyeceğini gösterirken RDT'de bir belgeyi canlı tutar. Belgede hiyerarşi veya öğe kimliği olmasa bile okuma kilidi ayarlayabilirsiniz. Bu özellik, belge herhangi bir hiyerarşiye ait olmadan bellekte bir belgeyi açıp RDT'ye girmenizi sağlar. Bu özellik nadiren kullanılır.|
|Kilit tutucu|Arabirim <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> örneği. Kilit tutucu, belgeleri düzenleyicinin dışında açan ve bunları düzenleme deki sihirbazlar gibi özellikler tarafından uygulanır. Kilit tutucu özelliği, belgenin hala düzenlenirken kapatılmasını önlemek için belgeye düzenleme kilidi eklemesine olanak tanır. Normalde, düzenleme kilitleri yalnızca belge pencereleri (yani düzenleyiciler) tarafından eklenir.|

 RDT'deki her girişin, genellikle projedeki tek düğüme karşılık gelen benzersiz bir hiyerarşisi veya öğe kimliği vardır. Düzenleme için kullanılabilen tüm belgeler genellikle bir hiyerarşiye aittir. RDT denetiminde yapılan girişler, hangi proje, daha doğrusu hangi hiyerarşi, şu anda düzenlenen belge veri nesnesinin sahibidir. RDT'deki bilgileri kullanarak, IDE bir belgenin aynı anda birden fazla proje tarafından açılmasını engelleyebilir.

 Hiyerarşi ayrıca verilerin kalıcılığını da denetler ve **Kaydet** ve **Kaydet** iletişim kutularını güncelleştirmek için RDT'deki bilgileri kullanır. Kullanıcılar bir belgeyi değiştirip **Dosya** menüsünden **Çıkış** komutunu seçtiğinde, IDE bunları değişiklikleri **kaydet** iletişim kutusunu n için ister ve bunları şu anda değiştirilen tüm projeleri ve proje öğelerini gösterir. Bu, kullanıcıların belgelerden hangisini kaydedeceğini seçmelerine olanak tanır. Kaydolunacak belgelerin listesi (diğer bir şekilde, değişiklikler olan belgeler) RDT'den oluşturulur. Uygulamadan çıktıktan sonra **Değişiklikleri Kaydet** iletişim kutusunda görmeyi beklediğiniz öğelerin RDT'de kayıtları olmalıdır. RDT, hangi belgelerin kaydedildiğini ve kullanıcıdan her belge için Bayraklar girişinde belirtilen değerleri kullanarak bir kaydetme işlemi hakkında soru sorulup sorulmadığını koordine eder. RDT bayrakları hakkında daha fazla <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> bilgi için numaralandırmaya bakın.

## <a name="edit-locks-and-read-locks"></a>Kilitleri Ve Okuma Kilitlerini Edin
 Kilitleri edin ve kilitleri okuyun RDT'de yer alıyor. Belge penceresi, edit kilidine artış lar ve kararnameler atar. Böylece, bir kullanıcı yeni bir belge penceresi açtığında, düzenleme kilidi sayısı bir oranında artarak. Edit kilitlerinin sayısı sıfıra ulaştığında, hiyerarşinin verileri kalıcı hale getirmek veya ilişkili belgeye kaydetmek için işaretlenir. Hiyerarşi daha sonra, dosya olarak veya depodaki bir öğe olarak kalıcılık da dahil olmak üzere verileri herhangi bir şekilde kalıcı olarak sürebilirsiniz. Kilitleri ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> okuma <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> kilitleri eklemek için arabirimdeki <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> yöntemi ve bu kilitleri kaldırmak için yöntemi kullanabilirsiniz.

 Normalde, bir düzenleyicinin belge penceresi anında olduğunda, pencere çerçevesi rdt'deki belge için otomatik olarak bir edit kilidi ekler. Ancak, standart belge penceresi kullanmayan bir belgenin özel bir görünümünü oluşturursanız (diğer <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> bir şekilde arabirimi uygulamaz), kendi edit kilidinizi ayarlamanız gerekir. Örneğin, bir sihirbazda, bir belge düzenleyicide açılmadan düzenlenir. Belge kilitlerinin sihirbazlar ve benzer varlıklar tarafından açılabilmesi için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> bu varlıkların arabirimi uygulaması gerekir. Belge kilit tutucunuzu kaydetmek <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> için yöntemi arayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> ve uygulamanızdan geçirin. Bunu yapmak, belge kilit tutucunuzu RDT'ye ekler. Belge kilidi tutucusu uygulamak için başka bir senaryo, bir belgeyi özel bir araç penceresinden açmanızdır. Bu durumda, araç penceresinin belgeyi kapatmasını sağlayamamaktadır. Ancak, RDT'de belge kilidi tutucu suolarak kaydolarak, IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> belgenin kapatılmasını istemiyle yöntemuygulamanızı çağırabilir.

## <a name="other-uses-of-the-running-document-table"></a>Çalışan Belge Tablosunun Diğer Kullanımalanları
 IDE'deki diğer varlıklar belgeler hakkında bilgi almak için RDT'yi kullanır. Örneğin, kaynak denetim yöneticisi, dosyanın en yeni sürümünü aldıktan sonra, sistem düzenleyicide bir belgeyi yeniden yüklemek için sistem söylemek için RDT kullanır. Bunu yapmak için kaynak denetim yöneticisi RDT'deki dosyaları arar ve bunlardan herhangi birinin açık olup olmadığını görür. Bunlar varsa, daha sonra kaynak denetim yöneticisi önce hiyerarşi yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> uygular görmek için denetler. Proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> yöntemi uygulamıyorsa, kaynak denetim yöneticisi doğrudan belge veri <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> nesnesi üzerinde yöntemin uygulanmasını denetler.

 IDE, bir kullanıcı bu belgeyi isterse, açık bir belgeyi yeniden ortaya çıkarmak (öne getirmek) için RDT'yi de kullanır. Daha fazla bilgi için Dosya [Komutunu Aç'ı Kullanarak Dosyaları Görüntüleme'ye](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)bakın. RDT'de bir dosyanın açık olup olmadığını belirlemek için aşağıdakilerden birini yapın.

- Öğenin açık olup olmadığını öğrenmek için belge lakabını (diğer bir şekilde tam belge yolu) sorgula.

- Proje sisteminden tam belge yolunu sormak için hiyerarşiyi veya öğe kimliğini kullanın ve ardından maddeyi RDT'de arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [RDT_ReadLock Kullanımı](../../extensibility/internals/rdt-readlock-usage.md)
- [Kalıcılık ve Çalıştırılan Belge Tablosu](../../extensibility/internals/persistence-and-the-running-document-table.md)
