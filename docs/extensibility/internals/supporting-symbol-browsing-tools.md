---
title: Sembol Tarama Araçlarını Destekleme | Microsoft Dokümanlar
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4998e47ccd6f99df2710833c18975d57e3bb92f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704775"
---
# <a name="supporting-symbol-browsing-tools"></a>Sembol Tarama Araçlarını Destekleme
**Object Browser**, **Class View**, Call **Browser** ve Find **Symbol Results** araçları Visual Studio'da sembol tarama özellikleri sağlar. Bu araçlar sembollerin hiyerarşik ağaç görünümlerini görüntüler ve ağaçtaki semboller arasındaki ilişkileri gösterir. Semboller ad alanlarını, nesneleri, sınıfları, sınıf üyelerini ve çeşitli bileşenlerde bulunan diğer dil öğelerini temsil edebilir. Bileşenler Visual Studio projelerini, harici .NET Framework bileşenlerini ve türü (.tlb) kitaplıklarını içerir. Daha fazla bilgi için [bkz.](../../ide/viewing-the-structure-of-code.md)

## <a name="symbol-browsing-libraries"></a>Sembol Tarama Kitaplıkları
 Bir dil uygulayıcısı olarak, bileşenlerinizdeki sembolleri izleyen ve bir dizi arabirim aracılığıyla Visual Studio nesne yöneticisine sembol listelerini sağlayan kitaplıklar oluşturarak Visual Studio sembol tarama özelliklerini genişletebilirsiniz. Bir kitaplık <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> arabirimi tarafından açıklanır. Visual Studio nesne yöneticisi, kitaplıklardan verileri alarak ve düzenleyerek sembol tarama araçlarından gelen yeni veri isteklerine yanıt verir. Daha sonra araçları istenen verilerle doldurur veya güncelleştirir. Visual Studio nesne yöneticisine <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>başvuru almak için, servis kimliğini yönteme geçirin. <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> `GetService`

 Her kitaplık, tüm kitaplıklar hakkındaki bilgileri toplayan Visual Studio nesne yöneticisine kaydolmalıdır. Kitaplığı kaydetmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> yöntemi arayın. İsteği başlatan araca bağlı olarak Visual Studio nesne yöneticisi uygun kitaplığı bulur ve verileri ister. Veriler, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> arabirim tarafından açıklanan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] semboller listelerinde kitaplıklar ve nesne yöneticisi arasında seyahat eder.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Nesne yöneticisi, kitaplıklarda bulunan en güncel verileri yansıtacak şekilde sembol tarama araçlarını düzenli olarak yenilemekten sorumludur.

 Aşağıdaki diyagram, kitaplık ve Visual Studio nesne yöneticisi arasındaki istekler/veri alışverişi sürecinin temel öğelerinin bir örneğini içerir. Diyagramdaki arabirimler yönetilen kod uygulamasının bir parçasıdır.

 ![Kitaplık ve nesne yöneticisi arasındaki veri akışı](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Visual Studio nesne yöneticisine sembol listelerini sağlamak için, önce yöntemi arayarak kitaplığı <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> Visual Studio nesne yöneticisine kaydettirmelisiniz. Kitaplık kaydedildikten sonra, Visual Studio nesne yöneticisi kitaplığın yetenekleri hakkında belirli bilgiler ister. Örneğin, kitaplık bayraklarını ve desteklenen kategorileri <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> çağırarak ve yöntemleri çağırarak ister. Bir noktada, araçlardan biri bu kitaplıktan veri istediğinde, nesne yöneticisi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> yöntemi çağırarak üst düzey semboller listesini ister. Buna karşılık, kitaplık sembollerin bir listesini üretir ve arabirim aracılığıyla <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> Visual Studio nesne yöneticisine sunar. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Nesne <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> yöneticisi, yöntemi çağırarak listede kaç öğe olduğunu belirler. Aşağıdaki tüm istekler listedeki belirli bir maddeyle ilgilidir ve her istekteki madde dizin numarasını tedarik edin. Visual Studio nesne <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> yöneticisi, yöntemi çağırarak öğenin türü, erişilebilirliği ve diğer özellikleri hakkındaki bilgileri toplamaya devam eder.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> Yöntemi çağırarak öğenin adını belirler ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> yöntemi arayarak simge bilgilerini ister. Simge öğe adının solunda görüntülenir ve öğenin türünü, erişilebilirliği ve diğer özellikleri görüntüler.

 Nesne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yöneticisi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> belirli bir liste öğesinin genişletilebilir olup olmadığını ve küçük öğeleri olup olmadığını belirlemek için yöntemi çağırır. UI bir öğeyi genişletmek için bir istek gönderirse, nesne <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> yöneticisi yöntemi çağırarak alt simge listesini ister. Süreç, ağacın farklı kısımlarının isteğe bağlı olarak inşa edilmesiyle devam eder.

> [!NOTE]
> Yerel kod sembolü sağlayıcısını uygulamak <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> için, arabirimleri ve arabirimleri kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır:Nesne Yöneticisine Kitaplık Kaydetme](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Nasıl Yapılır: Kitaplık Tarafından Sağlanan Sembollerin Listelerini Nesne Yöneticisine Sunma](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Nasıl Yapılır: Bir Kitaplıktaki Sembolleri Tanımlama](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
