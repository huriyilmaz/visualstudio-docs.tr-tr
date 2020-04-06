---
title: Kaynak Kontrol Paketleri Modeli | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46845be1bc22a67d6703af12933945bdfcfa7f4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707067"
---
# <a name="model-for-source-control-packages"></a>Kaynak Denetimi Paketleri için Model
Aşağıdaki model, kaynak denetimi uygulamasının bir örneğini temsil eder. Modelde, uygulamanız gereken arabirimleri ve aramanız gereken ortam hizmetlerini görürsünüz. Tüm hizmetler gibi, aslında hizmet yolu ile elde belirli bir arabirimin yöntemleri diyoruz. Kaynak denetiminin nasıl gerçekleştirildiğini görmek için sınıfların adları tanımlanır.

 ![SCC&#95;TUP Örnekleri](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Örnek Kaynak Kontrol Projesi

## <a name="interfaces"></a>Arabirimler
 Aşağıdaki tabloda gösterilen arabirimlerin listesini kullanarak Visual Studio'da yeni proje türleri için kaynak denetimi uygulayabilirsiniz.

|Arabirim|Kullanım|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|(Kirli) dosyaları kaydetmeden veya değiştirmeden önce projeler ve editörler tarafından çağrılır. Bu arabirime <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> hizmet kullanılarak erişilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Bir dosya veya dizin eklemek, kaldırmak veya yeniden adlandırmak için izin istemek için projeler tarafından çağrılır. Bu arabirim, onaylanan bir ekleme, kaldırma veya yeniden adlandırma eylemi tamamlandığında ortamı bilgilendirmek için projeler tarafından da çağrılır. Bu <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> hizmet kullanılarak erişilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Projeler bir dosya veya dizini eklediğinde, yeniden adlandırDığında veya kaldırdığında bildirilecek şekilde kaydolan herhangi bir kuruluş tarafından uygulanır. Olay bildirimine kaydolmak <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>için .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Projeler tarafından kaynak denetim paketine kaydolmak ve kaynak denetim durumu hakkında bilgi almak için çağrılır. Bu arabirime <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> hizmet kullanılarak erişilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Proje tarafından, dosyalar hakkında bilgi için kaynak denetimi isteklerine yanıt vermek ve proje dosyası için gerekli kaynak denetim ayarlarını elde etmek için uygulanır.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)
