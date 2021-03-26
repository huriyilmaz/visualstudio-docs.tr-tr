---
title: Symbol-Browsing araçlarını destekleme | Microsoft Docs
description: Visual Studio, Visual Studio 'da simgeye göz atma özellikleri sağlar. Bileşeninizdeki semboller için bu özellikleri kitaplıklarla genişletmeyi öğrenin.
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
ms.workload:
- vssdk
ms.openlocfilehash: d54f56ae3bc5fd5956f67400d84edfd4c8c9e55c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080573"
---
# <a name="supporting-symbol-browsing-tools"></a>Sembol Tarama Araçlarını Destekleme
**Nesne tarayıcısı**, **sınıf görünümü**, **çağrı tarayıcısı** ve **bulma sembol sonuçları** araçları, Visual Studio 'da sembol tarama özellikleri sağlar. Bu araçlar, sembollerin hiyerarşik ağaç görünümlerini görüntüler ve ağaçtaki semboller arasındaki ilişkileri gösterir. Semboller, çeşitli bileşenlerde bulunan ad alanlarını, nesneleri, sınıfları, sınıf üyelerini ve diğer dil öğelerini temsil edebilir. Bileşenler Visual Studio projeleri, dış .NET Framework bileşenleri ve tür (. tlb) kitaplıklarını içerir. Daha fazla bilgi için bkz. [kod yapısını görüntüleme](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Symbol-Browsing kitaplıkları
 Bir dil uygulayıcısı olarak, bileşenlerinizde sembolleri izleyen ve bir arabirimler kümesi aracılığıyla Visual Studio nesne Yöneticisi ' ne sembol listesi sağlayan kitaplıklar oluşturarak Visual Studio sembol tarama yeteneklerini genişletebilirsiniz. Bir kitaplık, arabirimi tarafından açıklanmıştır <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> . Visual Studio nesne Yöneticisi, kitaplıklardaki verileri alarak ve düzenleyerek sembol tarama araçlarından yeni verilere yönelik isteklere yanıt verir. Ardından, araçları istenen verilerle doldurur veya güncelleştirir. Visual Studio nesne Yöneticisi 'ne bir başvuru almak için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> hizmet kimliğini `GetService` metoduna geçirin.

 Her kitaplığın, tüm kitaplıkların bilgilerini toplayan Visual Studio nesne Yöneticisi ile kaydolması gerekir. Bir kitaplığı kaydetmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> yöntemini çağırın. İsteği hangi aracın başlatdığına bağlı olarak, Visual Studio nesne Yöneticisi uygun kitaplığı ve istek verilerini bulur. Veriler, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arabirim tarafından tanımlanan semboller listesinde kitaplıklar ve nesne Yöneticisi arasında dolaşır <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Nesne Yöneticisi, kitaplıklarda bulunan en güncel verileri yansıtmak üzere sembol tarama araçlarını düzenli aralıklarla yenilemekten sorumludur.

 Aşağıdaki diyagramda, bir kitaplık ve Visual Studio nesne yöneticisi arasındaki isteklerin/veri değişimi sürecinin temel öğelerinin bir örneği bulunur. Diyagramdaki arabirimler, yönetilen kod uygulamasının bir parçasıdır.

 ![Bir kitaplık ile nesne yöneticisi arasındaki veri akışı](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Visual Studio nesne Yöneticisi ' ne sembol listesi sağlamak için, öncelikle yöntemini çağırarak kitaplığı Visual Studio nesne Yöneticisi ile kaydetmeniz gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> . Kitaplık kaydedildikten sonra, Visual Studio nesne Yöneticisi kitaplığın özellikleri hakkında belirli bilgiler ister. Örneğin, ve yöntemlerini çağırarak kitaplık bayraklarını ve desteklenen kategorileri ister <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> . Bir noktada, araçlardan biri bu kitaplıktan veri istediğinde, nesne Yöneticisi, metodu çağırarak simgelerin en üst düzey listesini ister <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> . Yanıt olarak, kitaplık bir sembol listesi oluşturur ve bunu arabirim aracılığıyla Visual Studio nesne Yöneticisi 'nde gösterir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Nesne Yöneticisi, yöntemi çağırarak listede kaç öğe olduğunu belirler <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> . Aşağıdaki tüm istekler listedeki belirli bir öğeyle ilgilidir ve her istekte öğe dizin numarasını sağlar. Visual Studio nesne Yöneticisi, yöntemi çağırarak, bu öğenin türü, erişilebilirliği ve diğer özellikleri hakkında bilgi toplamaya devam eder <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> .

 Yöntemi çağırarak öğenin adını belirler <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> ve yöntemi çağırarak simge bilgilerini ister <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> . Simge öğe adının solunda görüntülenir ve öğenin türünü, erişilebilirliği ve diğer özellikleri gösterir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Nesne Yöneticisi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> belirli bir liste öğesinin Genişletilebilir olup olmadığını ve alt öğeleri olup olmadığını belirleme yöntemini çağırır. UI bir öğeyi genişletmek için bir istek gönderirse, nesne Yöneticisi, metodu çağırarak sembol alt listesini ister <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> . İşlem, ağacın üzerine inşa edilen farklı bölümleriyle devam eder.

> [!NOTE]
> Yerel kod sembol sağlayıcısını uygulamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> arabirimlerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır:Nesne Yöneticisine Kitaplık Kaydetme](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Nasıl Yapılır: Kitaplık Tarafından Sağlanan Sembollerin Listelerini Nesne Yöneticisine Sunma](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Nasıl Yapılır: Bir Kitaplıktaki Sembolleri Tanımlama](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
