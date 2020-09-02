---
title: 'Nasıl yapılır: geri alma yönetimini uygulama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3d56ae02718f5dfdf373eeeb6aff774d11931e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831128"
---
# <a name="how-to-implement-undo-management"></a>Nasıl Yapılır: Geri Alma Yönetimini Uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Geri alma yönetimi için kullanılan birincil arabirim, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> ortam tarafından uygulanan olur. Geri alma yönetimini desteklemek için, ayrı geri alma birimleri (yani, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> birden çok bireysel adım içerebilen) uygulayın.  
  
 Geri alma yönetimini uyguladığınızda, Düzenleyicinizde birden fazla görünümü destekleyip desteklemediğine bağlı olarak farklılık gösterir. Her uygulamayla ilgili yordamlar aşağıdaki bölümlerde ayrıntılı olarak verilmiştir.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Düzenleyicinin tek bir görünümü desteklediği durumlar  
 Bu senaryoda, düzenleyici birden fazla görünümü desteklemez. Yalnızca bir düzenleyici ve bir belge vardır ve geri almayı destekler. Geri alma yönetimini uygulamak için aşağıdaki yordamı kullanın.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Tek bir görünüm Düzenleyicisi için geri alma yönetimini desteklemek için  
  
1. `QueryInterface` `IServiceProvider` `IOleUndoManager` Belge görünümü nesnesinden geri alma yöneticisine () erişmek için, için pencere çerçevesindeki arabirimde ' i çağırın `IID_IOLEUndoManager` .  
  
2. Bir görünüm bir pencere çerçevesine eklendiğinde, için çağırmak için kullanabileceği bir site işaretçisi alır `QueryInterface` `IServiceProvider` .  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Düzenleyicinin birden çok görünümü desteklediği durumlar  
 Belge ve görünüm ayrımı varsa, genellikle belgenin kendisiyle ilişkili bir geri alma yöneticisi vardır. Tüm geri alma birimleri belge verileri nesnesiyle ilişkili bir geri alma Yöneticisi üzerine yerleştirilir.  
  
 Her bir görünüm için bir tane olmak üzere, geri alma yöneticisini sorgulama görünümü yerine, belge verileri nesnesi <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> geri alma yöneticisinin örneğini oluşturmak için, CLSID_OLEUndoManager bir sınıf tanımlayıcısı belirterek çağırır. Sınıf tanımlayıcısı, OCUNDOıD. h dosyasında tanımlanmıştır.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>Kendi geri alma yöneticisi örneğinizi oluşturmak için kullanırken, geri alma yöneticinizin ortama bağlamak için aşağıdaki yordamı kullanın.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Geri alma yöneticinizin ortama bağlama  
  
1. `QueryInterface`İçin öğesinden döndürülen nesnede çağırın <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> `IID_IOleUndoManager` . İşaretçiyi öğesine depolayın <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> .  
  
2. `QueryInterface`İçin öğesini `IOleUndoManager` çağırın `IID_IOleCommandTarget` . İşaretçiyi öğesine depolayın <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
3. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> `IOleCommandTarget` Aşağıdaki StandardCommandSet97 komutları için uygulamanızı ve saklı arabirime geçiş yapın:  
  
   - cmdidUndo  
  
   - cmdidMultiLevelUndo  
  
   - Cmdidyinele  
  
   - Cmdidmultilevelyinele  
  
   - cmdidMultiLevelUndoList  
  
   - cmdidMultiLevelRedoList  
  
4. `QueryInterface`İçin öğesini `IOleUndoManager` çağırın `IID_IVsChangeTrackingUndoManager` . İşaretçiyi öğesine depolayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> .  
  
    ,, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> Ve yöntemlerini çağırmak için işaretçisini kullanın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> .  
  
5. `QueryInterface`İçin öğesini `IOleUndoManager` çağırın `IID_IVsLinkCapableUndoManager` .  
  
6. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A>Belgeyi, Ayrıca, arabirimini de uygulamalıdır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> . Belgeniz kapatıldığında, öğesini çağırın `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient` .  
  
7. Belgeniz kapatıldığında, `QueryInterface` için geri alma yöneticinize çağrı yapın `IID_IVsLifetimeControlledObject` .  
  
8. Çağrısı yapın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A> .  
  
9. Belgede değişiklik yapıldığında, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> bir sınıf ile yöneticiye çağrı yapın `OleUndoUnit` . <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>Yöntemi nesnesine bir başvuru tutar, bu nedenle genellikle hemen sonrasında yayınlayamazsınız <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> .  
  
   `OleUndoManager`Sınıfı, tek bir geri alma yığın örneğini temsil eder. Bu nedenle, geri alma veya yineleme için izlenmekte olan veri varlığı başına bir geri alma Yöneticisi nesnesi vardır.  
  
> [!NOTE]
> Geri alma Yöneticisi nesnesi metin Düzenleyicisi tarafından kapsamlı olarak kullanıldığında, metin Düzenleyicisi için belirli bir desteği olmayan genel bir bileşendir. Çok düzeyli geri alma veya yineleme desteklemek istiyorsanız bu nesneyi kullanarak bunu yapabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Nasıl Yapılır: Geri Alma Yığınını Temizleme](../extensibility/how-to-clear-the-undo-stack.md)
