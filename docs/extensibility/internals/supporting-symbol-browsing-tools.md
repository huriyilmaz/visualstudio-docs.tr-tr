---
title: Symbol-Browsing Araçları | Microsoft Docs
description: Visual Studio' içinde sembol tarama Visual Studio. Bileşenlerinizin sembolleri için kitaplıklarla bu özellikleri genişletmeyi öğrenin.
ms.custom: SEO-VS-2020
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9b8383158773e088b1bfd2e5c955ff224c6800ad
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626049"
---
# <a name="supporting-symbol-browsing-tools"></a>Sembol Tarama Araçlarını Destekleme
**Object Browser**, **Sınıf Görünümü**, **Çağrı Tarayıcısı** ve **Sembol** Sonuçlarını Bul araçları, Visual Studio. Bu araçlar sembollerin hiyerarşik ağaç görünümlerini görüntüler ve ağaçtaki semboller arasındaki ilişkileri gösterir. Semboller ad alanlarını, nesneleri, sınıfları, sınıf üyelerini ve çeşitli bileşenlerde bulunan diğer dil öğelerini temsil eder. Bileşenler arasında Visual Studio, dış .NET Framework bileşenleri ve tür (.tlb) kitaplıkları yer almaktadır. Daha fazla bilgi için [bkz. Kod Yapısını Görüntüleme.](../../ide/viewing-the-structure-of-code.md)

## <a name="symbol-browsing-libraries"></a>Symbol-Browsing Kitaplıkları
 Dil uygulayıcı olarak, Visual Studio bileşenlerinizin simgelerini takip eden kitaplıklar oluşturarak ve arabirim kümesi aracılığıyla Visual Studio nesne yöneticisine sembol listesi sağlayan kitaplıklar oluşturarak Visual Studio sembol tarama özelliklerini genişletebilirsiniz. Kitaplık, arabirim tarafından <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> açıklanmıştır. Nesne Visual Studio yöneticisi, kitaplıklardan veri edinerek ve düzenleyerek sembol tarama araçlarından yeni veri isteklerine yanıt verir. Daha sonra araçları istenen verilerle doldurmak veya güncelleştirmek için kullanılır. nesne yöneticisine bir Visual Studio almak <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> için, hizmet <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> kimliğini yöntemine `GetService` iletir.

 Her kitaplığın, tüm Visual Studio toplayan nesne yöneticisine kaydolması gerekir. Bir kitaplığı kaydetmek için yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> arayın. İstek hangi aracın başlattığına bağlı olarak, Visual Studio nesne yöneticisi uygun kitaplığı bulur ve verileri istekler. Veriler, arabirim tarafından açıklanan sembollerin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] listelerinde kitaplıklar ve nesne yöneticisi arasında <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> ilerler.

 Nesne yöneticisi, kitaplıklarda bulunan en güncel verileri yansıtmak için sembol tarama araçlarını [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] düzenli aralıklarla yenilemeden sorumludur.

 Aşağıdaki diyagramda, bir kitaplık ve veri kaynağı nesne yöneticisi arasındaki istek/veri değişimi işleminin Visual Studio örneği yer almaktadır. Diyagramda arabirimler, yönetilen kod uygulamasının bir parçası.

 ![Kitaplık ve nesne yöneticisi arasındaki veri akışı](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Visual Studio nesne yöneticisine simge listelerini sağlamak için, önce yöntemini çağırarak kitaplığı Visual Studio nesne yöneticisine kaydetmeniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> gerekir. Kitaplık kaydedildikten sonra, Visual Studio yöneticisi kitaplığın özellikleri hakkında belirli bilgileri talep eder. Örneğin, ve yöntemlerini çağırarak kitaplık bayraklarını ve desteklenen kategorileri <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> talep ediyor. Bir noktada, araçlardan biri bu kitaplıktan veri isteğinde bulundurarak nesne yöneticisi yöntemini çağırarak en üst düzey sembollerin listesini <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> ister. Yanıt olarak, kitaplık sembollerin bir listesini üretir ve arabirim aracılığıyla Visual Studio nesne yöneticisine <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> gösterir. Nesne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yöneticisi, yöntemini çağırarak listede kaç öğe olduğunu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> belirler. Aşağıdaki tüm istekler, listede yer alan bir öğeyle ilgilidir ve her istekte öğe dizini numarasını sağlar. Nesne Visual Studio, yöntemini çağırarak öğenin türü, erişilebilirliği ve diğer özellikleriyle ilgili bilgileri toplamaya <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> devam eder.

 yöntemini çağırarak öğenin adını belirler <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> ve yöntemini çağırarak simge bilgilerini talep <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> ediyor. Simge öğe adının sol tarafından görüntülenir ve öğenin türünü, erişilebilirliği ve diğer özellikleri gösterir.

 Nesne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yöneticisi, belirli bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> liste öğesinin genişletilebilir olup olmadığını ve alt öğeleri olup olmadığını belirlemek için yöntemini arar. Kullanıcı arabirimi bir öğeyi genişletmek için bir istek gönderirse, nesne yöneticisi yöntemini çağırarak sembollerin alt listesini <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> talep eder. İşlem, ağacın isteğe bağlı olarak farklı bölümleriyle devam eder.

> [!NOTE]
> Yerel kod sembol sağlayıcısı uygulamak için ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> arabirimlerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır:Nesne Yöneticisine Kitaplık Kaydetme](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Nasıl Yapılır: Kitaplık Tarafından Sağlanan Sembollerin Listelerini Nesne Yöneticisine Sunma](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Nasıl Yapılır: Bir Kitaplıktaki Sembolleri Tanımlama](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
