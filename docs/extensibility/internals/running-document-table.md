---
title: Belge tablosu çalıştırılıyor | Microsoft Docs
description: Visual Studio ıde 'nin bellekte bulunan tüm açık belgeleri içeren çalışan belge tablosunu nasıl koruduğu hakkında bilgi edinin.
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
ms.openlocfilehash: b087ab396920cbf25d0559b74915a17606b472ee
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049590"
---
# <a name="running-document-table"></a>Çalıştırılan Belge Tablosu
IDE, çalışmakta olan belge tablosu (RDT) adlı dahili bir yapıda açık olan tüm belgelerin listesini tutar. Bu liste, bu belgelerin Şu anda düzenlenip düzenlenmediğine bakılmaksızın bellekteki tüm açık belgeleri içerir. Belge, proje veya ana proje dosyası (örneğin, bir. vcxproj dosyası) dahil olmak üzere kalıcı olan herhangi bir öğedir.

## <a name="elements-of-the-running-document-table"></a>Çalışan belge tablosunun öğeleri
 Çalışan belge tablosu aşağıdaki girişleri içerir.

|Öğe|Açıklama|
|-------------|-----------------|
|Belge bilinen adı|Belge verileri nesnesini benzersiz bir şekilde tanımlayan bir dize. Bu, dosyaları yöneten bir proje sistemi için mutlak dosya yolu olacaktır (örneğin, C:\myproject\dosyam). Bu dize, bir veritabanındaki saklı yordamlar gibi dosya sistemleri dışındaki depolarda kaydedilen projeler için de kullanılır. Bu durumda, proje sistemi tanıyabileceği benzersiz bir dizeyi ve belgeyi nasıl depolayacağınızı belirlemede büyük olasılıkla ayrıştırılabilir.|
|Hiyerarşi sahibi|Bir arabirim tarafından temsil edildiği gibi, belgenin sahibi olan hiyerarşi nesnesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .|
|Öğe KIMLIĞI|Hiyerarşi içindeki belirli bir öğe için öğe tanımlayıcısı. Bu değer, bu belgenin sahibi olan hiyerarşideki tüm belgeler arasında benzersizdir, ancak bu değerin farklı hiyerarşiler genelinde benzersiz olması garanti edilmez.|
|Belge veri nesnesi|En azından bu bir `IUnknown`<br /><br /> nesne. IDE, `IUnknown` özel düzenleyicinin belge verileri nesnesi için arabirimin ötesinde belirli bir arabirim gerektirmez. Ancak, standart bir düzenleyicide, uygulamanın, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> dosyanın Kalıcılık çağrılarını projeden işlemesi için arabirimin uygulanması gerekir. Daha fazla bilgi için bkz. [Standart bir belgeyi kaydetme](../../extensibility/internals/saving-a-standard-document.md).|
|Bayraklar|Belgenin kaydedilip kaydedilmediğini denetleyen bayraklar, bir okuma veya düzenleme kilidi uygulanıp uygulanmadığını ve bu şekilde, bir RDT 'e girişler eklendiğinde belirtilebilir. Daha fazla bilgi için bkz <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> . sabit listesi.|
|Kilit sayısını Düzenle|Düzenleme kilidi sayısı. Bir düzenleme kilidi, bazı düzenleyicide belgenin düzenlenmek üzere açık olduğunu gösterir. Düzen sayısı, sıfır olarak geçerse, değişiklik yapıldığında kullanıcıdan belgeyi kaydetmesi istenir. Örneğin, **yeni pencere** komutunu kullanarak bir düzenleyicide bir belgeyi her açışınızda, bu belge için RDT 'deki bir düzenleme kilidi eklenir. Bir düzenleme kilidinin ayarlaniçin, belgenin bir hiyerarşi veya öğe KIMLIĞI olması gerekir.|
|Kilit sayısını oku|Okuma kilidi sayısı. Okuma kilidi, belgenin bir sihirbaz gibi bazı mekanizmayı okumakta olduğunu gösterir. Okuma kilidi, belgenin düzenlenemediğini belirten bir belgeyi RDT 'de canlı tutar. Belgenin bir hiyerarşisi veya öğe KIMLIĞI olmasa bile, bir okuma kilidi ayarlayabilirsiniz. Bu özellik, bellekteki bir belgeyi açmanıza ve herhangi bir hiyerarşiye ait olan belge olmadan RDT 'e girmenize olanak sağlar. Bu özellik nadiren kullanılır.|
|Kilit sahibi|Bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> arabirimin örneği. Kilit sahibi, bir düzenleyici dışında belge açan ve düzenleyen sihirbazlar gibi özellikler tarafından uygulanır. Kilit sahibi, özelliğin belge hala düzenlenirken kapanmasını engellemek için belgeye düzenleme kilidi eklemesine izin verir. Normalde, düzenleme kilitleri yalnızca belge pencereleri (yani, düzenleyiciler) tarafından eklenir.|

 RDT içindeki her girdinin, genellikle projedeki bir düğüme karşılık gelen benzersiz bir hiyerarşi veya öğe KIMLIĞI vardır. Düzenlemede kullanılabilen tüm belgeler genellikle bir hiyerarşiye aittir. RDT 'de yapılan girişler, hangi projenin veya daha doğru bir şekilde (hangi hiyerarşide düzenlenmekte olan belge verisi nesnesine sahip olduğunu denetler. , RDT 'deki bilgileri kullanarak IDE, bir belgenin aynı anda birden fazla proje tarafından açılmasını önleyebilir.

 Hiyerarşi Ayrıca verilerin kalıcılığını denetler ve **Kaydet** ve **farklı kaydet** iletişim kutularını güncelleştirmek için RDT 'teki bilgileri kullanır. Kullanıcılar bir belgeyi değiştirdiğinde ve sonra **Dosya** menüsünden **Çıkış** komutunu seçtiğinizde, IDE, o anda değiştirilen tüm projeleri ve proje öğelerini göstermek için **Değişiklikleri Kaydet** iletişim kutusunu sorar. Bu, kullanıcıların kaydedilecek belgeleri seçmesine olanak sağlar. Kaydedilecek belgelerin listesi (yani, değişiklikler içeren belgeler) RDT 'den oluşturulur. Uygulamadan çıkıldıktan sonra **Değişiklikleri Kaydet** iletişim kutusunda görmeyi düşündüğünüz tüm öğeler RDT 'de kayıtlar içermelidir. RDT, hangi belgelerin kaydedildiğini ve kullanıcıdan her belge için flags girişinde belirtilen değerleri kullanarak bir Kaydet işlemi isteyip istemediğiniz sorulur. RDT bayrakları hakkında daha fazla bilgi için bkz <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> . sabit listesi.

## <a name="edit-locks-and-read-locks"></a>Kilitleri Düzenle ve kilitleri oku
 Düzenleme kilitleri ve okuma kilitleri, RDT 'de bulunur. Belge penceresi, düzenleme kilidini artırır ve azaltır. Bu nedenle, bir Kullanıcı yeni bir belge penceresi açtığında, düzenleme kilidi sayısı bir artar. Düzenleme kilidi sayısı sıfıra ulaştığında, hiyerarşide devam etmek veya ilişkili belge için verileri kaydetmek için hiyerarşi sinyali verilir. Hiyerarşi daha sonra verileri bir dosya olarak veya depodaki bir öğe olarak kalıcı olarak herhangi bir şekilde kalıcı hale getirebilirler. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A>Arabirim içindeki yöntemi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> düzenleme kilitleri ve okuma kilitleri eklemek ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> Bu kilitleri kaldırma yöntemi eklemek için kullanabilirsiniz.

 Normalde, bir düzenleyicinin belge penceresi örneği oluşturulduğunda, pencere çerçevesi otomatik olarak RDT 'deki belge için bir düzenleme kilidi ekler. Ancak, bir belgenin standart belge penceresi kullanmayan (yani arabirimini uygulamadığından) özel bir görünümünü oluşturursanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> , kendi düzenleme kilidinizi ayarlamanız gerekir. Örneğin, bir sihirbazda bir belge düzenleyicide açılmaksızın düzenlenir. Belge kilitlerinin sihirbazlar ve benzer varlıklar tarafından açılabilmesi için, bu varlıkların arabirimini uygulaması gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> . Belge kilidi sahibini kaydetmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> yöntemini çağırın ve uygulamanızda geçiş yapın <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> . Bunun yapılması, belge kilidi sahibini RDT 'e ekler. Belge kilidi sahibini uygulamaya yönelik başka bir senaryo, bir belgeyi özel bir araç penceresi aracılığıyla açmanız durumunda olur. Bu örnekte, araç penceresini belgeyi kapatırsınız. Ancak, RDT 'de bir belge kilidi tutucusu olarak kaydolarak, IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> belgenin kapatılmasını istemek için yönteminin uygulamanızı çağırabilir.

## <a name="other-uses-of-the-running-document-table"></a>Çalışan belge tablosunun diğer kullanımları
 IDE 'deki diğer varlıklar, belgeler hakkında bilgi edinmek için RDT 'yi kullanır. Örneğin, kaynak denetimi Yöneticisi, dosyayı, dosyanın en yeni sürümünü aldıktan sonra düzenleyicide bir belgeyi yeniden yüklemesine söylemek için RDT 'yi kullanır. Bunu yapmak için kaynak denetimi Yöneticisi, bunlardan herhangi birinin açık olup olmadığını görmek için RDT 'deki dosyaları arar. Bu durumda, kaynak denetimi Yöneticisi önce hiyerarşinin yöntemi uygulayıp uygulamadığını denetler <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> . Proje yöntemi uygulamadıysanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> , kaynak denetimi Yöneticisi <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> doğrudan belge veri nesnesi üzerinde yönteminin bir uygulamasını denetler.

 Ayrıca, bir Kullanıcı bu belgeyi isterse, IDE, bir açık belge (önüne getir) için RDT 'i de kullanır. Daha fazla bilgi için bkz. [Dosya Aç komutunu kullanarak dosyaları görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Bir dosyanın RDT 'de açık olup olmadığını anlamak için aşağıdakilerden birini yapın.

- Öğenin açık olup olmadığını bulmak için belgenin bilinen adı (tam belge yolu) sorgulayın.

- Proje sisteminden tam belge yolunu sormak için hiyerarşi veya öğe KIMLIĞINI kullanın ve ardından öğeyi RDT içinde bulun.

## <a name="see-also"></a>Ayrıca bkz.
- [RDT_ReadLock Kullanımı](../../extensibility/internals/rdt-readlock-usage.md)
- [Kalıcılık ve Çalıştırılan Belge Tablosu](../../extensibility/internals/persistence-and-the-running-document-table.md)
