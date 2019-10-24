---
title: Kaynak denetimi paketleri için model | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a9ae5f2704d625da2212e92626c33fb384ebbc5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726559"
---
# <a name="model-for-source-control-packages"></a>Kaynak Denetimi Paketleri için Model
Aşağıdaki model, kaynak denetimi uygulamasına bir örnek temsil eder. Modelinde, uygulamanız gereken arabirimleri ve çağırmanız gereken ortam hizmetlerini görürsünüz. Tüm hizmetler gibi, aslında hizmet yoluyla elde ettiğiniz belirli bir arabirimin yöntemlerini çağırabilirsiniz. Sınıfların adları, kaynak denetiminin nasıl yapıldığını görmeyi kolaylaştırmak için tanımlanır.

 ![SCC&#95;önyükleme örnekleri](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Örnek kaynak denetimi projesi

## <a name="interfaces"></a>Arabirimler
 Aşağıdaki tabloda gösterilen arabirimlerin listesini kullanarak Visual Studio 'da yeni proje türleriniz için kaynak denetimi uygulayabilirsiniz.

|Arabirim|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Dosyalar kaydedilmeden veya değiştirmeden önce projeler ve düzenleyicilerle çağırılır. Bu arabirime <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> hizmeti kullanılarak erişilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Bir dosya veya dizin ekleme, kaldırma veya yeniden adlandırma izni istemek için projeler tarafından çağırılır. Bu arabirim, bir onaylanan ekleme, kaldırma veya yeniden adlandırma eylemi tamamlandığında ortamı bilgilendirmek için projeler tarafından da çağrılır. @No__t_0 hizmeti kullanılarak erişilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Projeler bir dosya veya dizin ekler, yeniden adlandırdığınızda veya kaldırırken bildirim almak üzere kaydeden herhangi bir varlık tarafından uygulanır. Olay bildirimine kaydolmak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A> çağırın.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Kaynak denetim paketiyle kaydolmak ve kaynak denetimi durumu hakkında bilgi almak için projeler tarafından çağırılır. Bu arabirime <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> hizmeti kullanılarak erişilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Dosyalar hakkında bilgi edinmek ve proje dosyası için gereken kaynak denetimi ayarlarını almak için proje tarafından uygulanır.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)