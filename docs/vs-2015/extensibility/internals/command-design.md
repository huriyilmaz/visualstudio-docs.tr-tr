---
title: Komut tasarımı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6e9eaf69be62b38a880b07fd8eb51cfc9c256a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195068"
---
# <a name="command-design"></a>Komut Tasarımı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage 'a bir komut eklediğinizde, nerede görüneceğini, kullanılabilir olduğunda ve nasıl işleneceğini belirtmeniz gerekir.  
  
## <a name="defining-commands"></a>Komutları tanımlama  
 Yeni komutlar tanımlamak için VSPackage projenize bir Visual Studio komut tablosu (. vsct) dosyası ekleyin. Visual Studio paket şablonunu kullanarak bir VSPackage oluşturduysanız, proje bu dosyalardan birini içerir. Daha fazla bilgi için bkz [. Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio, bulduğu tüm. vsct dosyalarını birleştirir, böylece komutları görüntüleyebilir. Bu dosyalar VSPackage ikilisinden farklı olduğundan, Visual Studio 'Nun komutları bulmak için paketini yüklemesi gerekmez. Daha fazla bilgi için bkz. [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio, <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> menü kaynaklarını ve komutları tanımlamak için kayıt özniteliğini kullanır. Daha fazla bilgi için bkz. [uygulama](../../extensibility/internals/command-implementation.md).  
  
 Komutlar, çalışma zamanında çeşitli yollarla değiştirilebilir. Bunlar görüntülenebilir veya gizli, etkinleştirilebilir veya devre dışı bırakılabilir. Farklı metin veya simgeleri görüntüleyebilir veya farklı değerler içerebilir. Visual Studio VSPackage 'ı yüklemeden önce harika bir özelleştirme gerçekleştirilemeyebilir. Daha fazla bilgi için bkz. [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Komut Işleyicileri  
 Bir komut oluşturduğunuzda, komutunu yürütmek için bir olay işleyicisi sağlamanız gerekir. Kullanıcı komutu seçerse, uygun şekilde yönlendirilmelidir. Komut yönlendirmesi, bunu etkinleştirmek veya devre dışı bırakmak, onu gizlemek veya göstermek ve Kullanıcı bunu seçerse yürütmek için doğru VSPackage 'a gönderilmesi anlamına gelir. Daha fazla bilgi için bkz. [yönlendirme algoritması](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>Visual Studio komut ortamı  
 Visual Studio herhangi bir sayıda VSPackages barındırabilir ve her biri kendi komut kümesini katkıda bulunabilir. Ortam yalnızca geçerli göreve uygun olan komutları görüntüler. Daha fazla bilgi için bkz. [kullanılabilirlik](../../extensibility/internals/command-availability.md) ve [seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md).  
  
 Yeni komutlar, menüler, araç çubukları veya kısayol menülerini tanımlayan bir VSPackage, yerel veya yönetilen derlemelerdeki kaynaklara başvuran kayıt defteri girişleri aracılığıyla, yükleme sırasında Visual Studio 'ya ait komut bilgilerini sağlar. Her kaynak daha sonra bir Visual Studio komut tablosu (. vsct) dosyası derlerken üretilen bir ikili veri kaynağı (. CTO) dosyasına başvurur. Bu, Visual Studio 'Nun her yüklü VSPackage yüklemesine gerek duymadan birleştirilmiş komut kümeleri, menüler ve araç çubukları sağlamasına olanak sağlar.  
  
### <a name="command-organization"></a>Komut organizasyonu  
 Ortam komutları gruba, önceliğe ve menüye göre konumlandırır.  
  
- Gruplar, ilgili komutların mantıksal koleksiyonlarıdır, örneğin **Kes**, **Kopyala**ve **Yapıştır** komut grubu. Gruplar menülerde görüntülenen komutlardır.  
  
- Öncelik, bir gruptaki bireysel komutların menüde görünme sırasını belirler.  
  
- Menüler, gruplar için kapsayıcı olarak davranır.  
  
  Ortam, bazı komutları, grupları ve menüleri önceden tanımlar. Daha fazla bilgi için bkz. [varsayılan komut, Grup ve araç çubuğu yerleşimi](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
  Bir komut, birincil gruba atanabilir. Birincil grup, komutun konumunu ana menü yapısında ve **Özelleştir** iletişim kutusunda denetler. Bir komut, birden çok grupta görünebilir; Örneğin, bir komut ana menüde, kısayol menüsünde ve bir araç çubuğunda olabilir. Daha fazla bilgi için bkz. [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>Komut Yönlendirme  
 VSPackages için çağırma ve Yönlendirme komutları nesne örneklerine çağırma sürecinden farklıdır.  
  
 Ortam komutları, geçerli seçime dayalı olan en dıştaki (yerel) komut bağlamından ardışık olarak (genel) içeriğine yönlendirir. Komutu yürütebilecek ilk bağlam onu işleyen bir. Daha fazla bilgi için bkz. [yönlendirme algoritması](../../extensibility/internals/command-routing-algorithm.md).  
  
 Çoğu örnekte, ortam komutları arabirimini kullanarak işler <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . Komut yönlendirme şeması birçok farklı nesnenin komutları işlemesini sağladığından, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> herhangi bir sayıda nesne tarafından uygulanabilir. bunlar Microsoft ActiveX denetimlerini, pencere görünümü uygulamalarını, belge nesnelerini, proje hiyerarşilerini ve VSPackage nesnelerini (genel komutlar için) içerir. Bazı özel durumlarda (örneğin, bir hiyerarşideki yönlendirme komutları), <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirimin uygulanması gerekir.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Uygulama](../../extensibility/internals/command-implementation.md)|Bir VSPackage içinde komutların nasıl uygulanacağını açıklar.|  
|[Kullanılabilirlik](../../extensibility/internals/command-availability.md)|Visual Studio bağlamının hangi komutların kullanılabilir olduğunu nasıl belirlediğini açıklar.|  
|[Yönlendirme Algoritması](../../extensibility/internals/command-routing-algorithm.md)|Visual Studio komut yönlendirme mimarisinin, komutların farklı VSPackages tarafından nasıl işleneceğini açıklar.|  
|[Yerleştirme Yönergeleri](../../extensibility/internals/command-placement-guidelines.md)|Visual Studio ortamında komutların nasıl konumlandıralınacağını önerir.|  
|[VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|VSPackages 'ın Visual Studio komut mimarisini en iyi şekilde kullanmasını açıklar.|  
|[Varsayılan Komut, Grup ve Araç Çubuğu Yerleşimi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|VSPackages 'in Visual Studio 'Ya dahil olan komutları en iyi şekilde nasıl kullanabileceğinizi açıklar.|  
|[VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)|Visual Studio 'Nun VSPackages 'yi nasıl yüklediğini açıklar.|  
|[Visual Studio Komut Tablosu (.Vsct) Dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|VSPackages içindeki komutların yerleşimini ve görünümünü anlatmak için kullanılan XML tabanlı. vsct dosyaları hakkında bilgi sağlar.|
