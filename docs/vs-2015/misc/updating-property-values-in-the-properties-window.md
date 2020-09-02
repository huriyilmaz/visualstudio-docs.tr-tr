---
title: Özellikler penceresinde özellik değerleri güncelleştiriliyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 18ecf0a21c5b2d73bdf8e439d25765b6b275cbd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434195"
---
# <a name="updating-property-values-in-the-properties-window"></a>Özellikler penceresinde özellik değerlerini güncelleştirme
**Özellikler** penceresini Özellik değeri değişiklikleriyle eşitlenmiş halde tutmanın iki yolu vardır. Birincisi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ortam tarafından sağlanan araç ve Belge pencerelerinin erişimine ve oluşturulmasına dahil olmak üzere temel pencere işlevlerine erişim sağlayan arabirimi çağırmakta. Aşağıdaki adımlarda bu eşitleme işlemi açıklanır.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Isuishell kullanarak özellik değerleri güncelleştiriliyor  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Isuishell arabirimini kullanarak özellik değerlerini güncelleştirmek için  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , VSPackages, proje veya düzenleyicilerin araç veya belge pencereleri oluşturması veya numaralandırması gereken her zaman çağrı (hizmet aracılığıyla).  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> **Özellikler** penceresini, olay uygulamadan ve tetiklemeden bir proje (veya **Özellikler** penceresi tarafından gözatılan diğer herhangi bir seçili nesne) için özellik değişiklikleriyle eşitlenmiş halde tutmak <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> için uygulayın <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> .  
  
3. Yöntemi uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> hiyerarşi olayları için, hiyerarşinin uygulanmasını gerektirmeden istemci bildirimini oluşturun ve devre dışı bırakın <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .  
  
## <a name="updating-property-values-using-iconnection"></a>IConnection kullanarak özellik değerlerini güncelleştirme  
 **Özellikler** penceresini Özellik değeri değişiklikleriyle eşitlenmiş halde tutmanın ikinci yolu, `IConnection` giden arabirimlerin varlığını göstermek için bağlanılabilir nesneye uygulanır. Özellik adını yerelleştirmek isterseniz, nesnenizin içinden türetebilirsiniz <xref:System.ComponentModel.ICustomTypeDescriptor> . <xref:System.ComponentModel.ICustomTypeDescriptor>Uygulama, döndürdüğü Özellik tanımlayıcılarını değiştirebilir ve bir özelliğin adını değiştirebilir. Açıklamayı yerelleştirmek için, <xref:System.ComponentModel.DescriptionAttribute> Description özelliğinden türetilen ve geçersiz kılacak bir öznitelik oluşturun.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>IConnection arabirimini uygulama konusunda dikkat edilecek noktalar  
  
1. `IConnection` arabirimle bir Numaralandırıcı alt nesnesine erişim sağlar <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> . Ayrıca, her biri arabirimini uygulayan tüm bağlantı noktası alt nesnelerine erişim sağlar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> .  
  
2. Herhangi bir tarayıcı nesnesi, bir olay uygulamaktan sorumludur <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> . **Özellikler** penceresi aracılığıyla olay kümesi için öneri alınacaktır `IConnection` .  
  
3. Bir bağlantı noktası, uygulamasının uygulamasında kaç tane bağlantı (bir veya daha fazla) izin verdiğini denetler <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> . Yalnızca bir arabirime izin veren bir bağlantı noktası yönteminden dönebilir <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> .  
  
4. Bir istemci arabirimi `IConnection` ile bir Numaralandırıcı alt nesnesine erişim elde etmek için arabirimi çağırabilir <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> . <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>Daha sonra arabirim, her giden ARABIRIM kimliği (IID) için bağlantı noktalarını numaralandırmak üzere çağrılabilir.  
  
5. `IConnection` , bağlantı noktası alt nesnelerine <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> her gıden IID için arabirim ile erişim sağlamak için de çağrılabilir. Arabirim aracılığıyla <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> istemci, bağlanılabilir nesne ve istemcinin kendi eşitlemesine sahip bir danışmanlık döngüsünü başlatır veya sonlandırır. İstemci Ayrıca, <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> bildiği bağlantıları numaralandırmak için arabirimi ile bir Numaralandırıcı nesnesi elde etmek üzere arabirimi çağırabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellik penceresi seçim Izleme duyurusu](../misc/announcing-property-window-selection-tracking.md)   
 [Özellikleri Genişletme](../extensibility/internals/extending-properties.md)