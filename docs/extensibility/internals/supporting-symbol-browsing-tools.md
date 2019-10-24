---
title: Sembol tarama araçlarını destekleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ca171fa75adda3deef5b941852fc3e6c648c84c6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723076"
---
# <a name="supporting-symbol-browsing-tools"></a>Sembol Tarama Araçlarını Destekleme
**Nesne tarayıcısı**, **sınıf görünümü**, **çağrı tarayıcısı** ve **bulma sembol sonuçları** araçları, Visual Studio 'da sembol tarama özellikleri sağlar. Bu araçlar, sembollerin hiyerarşik ağaç görünümlerini görüntüler ve ağaçtaki semboller arasındaki ilişkileri gösterir. Semboller, çeşitli bileşenlerde bulunan ad alanlarını, nesneleri, sınıfları, sınıf üyelerini ve diğer dil öğelerini temsil edebilir. Bileşenler Visual Studio projeleri, dış .NET Framework bileşenleri ve tür (. tlb) kitaplıklarını içerir. Daha fazla bilgi için bkz. [kod yapısını görüntüleme](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Sembol tarama kitaplıkları
 Bir dil uygulayıcısı olarak, bileşenlerinizde sembolleri izleyen ve bir arabirimler kümesi aracılığıyla Visual Studio nesne Yöneticisi ' ne sembol listesi sağlayan kitaplıklar oluşturarak Visual Studio sembol tarama yeteneklerini genişletebilirsiniz. Bir kitaplık <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> arabirimi tarafından açıklanmıştır. Visual Studio nesne Yöneticisi, kitaplıklardaki verileri alarak ve düzenleyerek sembol tarama araçlarından yeni verilere yönelik isteklere yanıt verir. Ardından, araçları istenen verilerle doldurur veya güncelleştirir. Visual Studio nesne Yöneticisi 'ne bir başvuru almak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> hizmet KIMLIĞINI `GetService` metoduna geçirin.

 Her kitaplığın, tüm kitaplıkların bilgilerini toplayan Visual Studio nesne Yöneticisi ile kaydolması gerekir. Bir kitaplığı kaydetmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> yöntemi çağırın. İsteği hangi aracın başlatdığına bağlı olarak, Visual Studio nesne Yöneticisi uygun kitaplığı ve istek verilerini bulur. Veriler, kitaplıklar ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nesne Yöneticisi arasında <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> arabirimi tarafından tanımlanan simgelerin listelerinde dolaşır.

 @No__t_0 nesne Yöneticisi, kitaplıklarda bulunan en güncel verileri yansıtmak üzere sembol tarama araçlarını düzenli aralıklarla yenilemekten sorumludur.

 Aşağıdaki diyagramda, bir kitaplık ve Visual Studio nesne yöneticisi arasındaki isteklerin/veri değişimi sürecinin temel öğelerinin bir örneği bulunur. Diyagramdaki arabirimler, yönetilen kod uygulamasının bir parçasıdır.

 ![Bir kitaplık ile nesne yöneticisi arasındaki veri akışı](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Visual Studio nesne Yöneticisi ' ne sembol listesi sağlamak için, öncelikle <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> yöntemini çağırarak kitaplığı Visual Studio nesne Yöneticisi ile kaydetmeniz gerekir. Kitaplık kaydedildikten sonra, Visual Studio nesne Yöneticisi kitaplığın özellikleri hakkında belirli bilgiler ister. Örneğin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> yöntemlerini çağırarak kitaplık bayraklarını ve desteklenen kategorileri ister. Bir noktada, araçlardan biri bu kitaplıktan veri istediğinde, nesne Yöneticisi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> yöntemini çağırarak simgelerin en üst düzey listesini ister. Yanıt olarak, kitaplık bir sembol listesi oluşturur ve onu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> arabirimi aracılığıyla Visual Studio nesne Yöneticisi 'nde gösterir. @No__t_0 nesne Yöneticisi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> metodunu çağırarak listede kaç öğe olduğunu belirler. Aşağıdaki tüm istekler listedeki belirli bir öğeyle ilgilidir ve her istekte öğe dizin numarasını sağlar. Visual Studio nesne Yöneticisi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> metodu çağırarak, öğenin türü, erişilebilirliği ve diğer özellikleri hakkında bilgi toplamaya devam eder.

 @No__t_0 yöntemini çağırarak ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> metodunu çağırarak simge bilgilerini istediğinde öğenin adını belirler. Simge öğe adının solunda görüntülenir ve öğenin türünü, erişilebilirliği ve diğer özellikleri gösterir.

 @No__t_0 nesne Yöneticisi, belirli bir liste öğesinin Genişletilebilir olup olmadığını ve alt öğeleri olduğunu anlamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> yöntemini çağırır. UI bir öğeyi genişletmek için bir istek gönderirse, nesne Yöneticisi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> yöntemini çağırarak sembol alt listesini ister. İşlem, ağacın üzerine inşa edilen farklı bölümleriyle devam eder.

> [!NOTE]
> Yerel kod sembol sağlayıcısını uygulamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> arabirimlerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır:Nesne Yöneticisine Kitaplık Kaydetme](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Nasıl Yapılır: Kitaplık Tarafından Sağlanan Sembollerin Listelerini Nesne Yöneticisine Sunma](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Nasıl Yapılır: Bir Kitaplıktaki Sembolleri Tanımlama](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)