---
title: Komut Tasarımı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aa58813623dc8150cafb4fbfee6496d09f889ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709653"
---
# <a name="command-design"></a>Komut tasarımı
BIR VSPackage'a komut eklediğinizde, nerede görüneceğini, ne zaman kullanılabileceğini ve nasıl işleneceğini belirtmeniz gerekir.

## <a name="define-commands"></a>Komutları tanımlama
 Yeni komutlar tanımlamak için VSPackage projenize Visual Studio komut tablosu (*.vsct*) dosyası ekleyin. Visual Studio paket şablonu kullanarak bir VSPackage oluşturduysanız, proje bu dosyalardan birini içerir. Daha fazla bilgi için [Visual Studio komut tablosu (.vsct) dosyalarına](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)bakın.

 Visual Studio, bulduğu tüm *.vsct* dosyalarını komutları görüntüleyebilmek için birleştirir. Bu dosyalar VSPackage ikilisinden farklı olduğundan, Visual Studio komutları bulmak için paketi yüklemek zorunda değildir. Daha fazla bilgi için [VSPackages'In kullanıcı arabirimi öğelerini nasıl ekleyeceğini](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)görün.

 Visual Studio <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> menü kaynaklarını ve komutlarını tanımlamak için kayıt özniteliğini kullanır. Daha fazla bilgi için [Komut uygulamasına](../../extensibility/internals/command-implementation.md)bakın.

 Komutlar çalışma zamanında farklı şekillerde değiştirilebilir. Bunlar görüntülenebilir veya gizlenebilir, etkinleştirilebilir veya devre dışı bırakılır. Farklı metin veya simgeleri görüntüleyebilir veya farklı değerler içerebilirler. Visual Studio VSPackage'ınızı yüklemeden önce çok sayıda özelleştirme gerçekleştirilebilir. Daha fazla bilgi için [VSPackages'In kullanıcı arabirimi öğelerini nasıl ekleyeceğini](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)görün.

## <a name="command-handlers"></a>Komut işleyicileri
 Bir komut oluşturduğunuzda, komutu yürütmek için bir olay işleyicisi sağlamanız gerekir. Kullanıcı komutu seçerse, uygun şekilde yönlendirilmelidir. Bir komutu yönlendirme, komutu etkinleştirmek veya devre dışı etmek, gizlemek veya görüntülemek ve kullanıcı isterse yürütmek için doğru VSPackage'a göndermek anlamına gelir. Daha fazla bilgi için [bkz.](../../extensibility/internals/command-routing-algorithm.md)

## <a name="visual-studio-command-environment"></a>Visual Studio komut ortamı
 Visual Studio herhangi bir sayıda VSPackages barındırabilir ve her biri kendi komut kümesine katkıda bulunabilir. Ortam yalnızca geçerli göreve uygun komutları görüntüler. Daha fazla bilgi için [Selection context objects](../../extensibility/internals/selection-context-objects.md) [bkz.](../../extensibility/internals/command-availability.md)

 Yeni komutları, menüleri, araç çubuklarını veya kısayol menülerini tanımlayan bir VSPackage, komut bilgilerini yerel veya yönetilen derlemelerde kaynaklara başvuran kayıt defteri girişleri aracılığıyla yükleme zamanında Visual Studio'ya sağlar. Her kaynak daha sonra bir Visual Studio komut tablosu (*.vsct*) dosyasını derlediğinizde üretilen bir ikili veri kaynağı (*.cto*) dosyasına başvurur. Bu, Visual Studio'nun yüklü her VSPackage'ı yüklemek zorunda kalmadan birleştirilmiş komut kümeleri, menüler ve araç çubukları sağlamasına olanak tanır.

### <a name="command-organization"></a>Komuta organizasyonu
 Ortam komutlarını gruba, önceliğe ve menüye göre konumlandırıyor.

- Gruplar, ilgili komutların mantıksal koleksiyonlarıdır(örneğin, **Kes,** **Kopyala**ve **Yapıştır** komut grubu). Gruplar menülerde görünen komutlardır.

- Öncelik, bir gruptaki tek tek komutların menüde görünme sırasını belirler.

- Menüler gruplar için kapsayıcı görevi görededir.

  Ortam, bazı komutları, grupları ve menüleri önceden tanımlar. Daha fazla bilgi için [Varsayılan komut, grup ve araç çubuğu yerleşimine](../../extensibility/internals/default-command-group-and-toolbar-placement.md)bakın.

  Bir komut birincil gruba atanabilir. Birincil grup, ana menü yapısında ve **Özelleştir** iletişim kutusunda komutun konumunu denetler. Bir komut birden çok grupta görünebilir; örneğin, bir komut ana menüde, kısayol menüsünde ve araç çubuğunda olabilir. Daha fazla bilgi için [VSPackages'In kullanıcı arabirimi öğelerini nasıl ekleyeceğini](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)görün.

### <a name="command-routing"></a>Komut yönlendirme
 VSPackages için komut çağırma ve yönlendirme işlemi nesne örneklerinde arama yöntemleri işleminden farklıdır.

 Ortam, komutları geçerli seçimi temel alan en içteki (yerel) komut bağlamından en dıştaki (genel) içeriğe sırayla yönlendirir. Komutu yürütebilen ilk bağlam, komutu işleyen bağlamdır. Daha fazla bilgi için [bkz.](../../extensibility/internals/command-routing-algorithm.md)

 Çoğu durumda, ortam <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi kullanarak komutları işler. Komut yönlendirme düzeni birçok farklı nesnenin komutları işlemesini <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> sağladığından, herhangi bir sayıda nesne tarafından uygulanabilir; bunlar arasında Microsoft ActiveX denetimleri, pencere görünümü uygulamaları, belge nesneleri, proje hiyerarşileri ve VSPackage nesnelerinin kendileri (genel komutlar için) yer almaktadır. Bazı özel durumlarda, örneğin, bir hiyerarşideki yönlendirme komutları, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirim uygulanmalıdır.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Komut uygulaması](../../extensibility/internals/command-implementation.md)|VSPackage'da komutların nasıl uygulanacağını açıklar.|
|[Komut kullanılabilirliği](../../extensibility/internals/command-availability.md)|Visual Studio bağlamında hangi komutların kullanılabilir olduğunu nasıl belirlediğini açıklar.|
|[Komut yönlendirme algoritması](../../extensibility/internals/command-routing-algorithm.md)|Visual Studio komut yönlendirme mimarisinin komutların farklı VSPackages tarafından ele alınmasına nasıl olanak sağladığını açıklar.|
|[Komut yerleştirme yönergeleri](../../extensibility/internals/command-placement-guidelines.md)|Visual Studio ortamında komutların nasıl konumlandırılabildiğini önerir.|
|[VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|VSPackages'ın Visual Studio komut mimarisini en iyi şekilde nasıl kullanabileceğini açıklar.|
|[Varsayılan komut, grup ve araç çubuğu yerleşimi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|VSPackages'ın Visual Studio'da bulunan komutları en iyi nasıl kullanabileceğini açıklar.|
|[VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)|Visual Studio'nun VSPackages'i nasıl yükleyebildiğini açıklar.|
|[Visual Studio komut tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|VSPackages'teki komutların düzenini ve görünümünü açıklamak için kullanılan XML tabanlı *.vsct* dosyaları hakkında bilgi sağlar.|
