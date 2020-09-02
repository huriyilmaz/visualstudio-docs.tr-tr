---
title: Basitleştirilmiş ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b8e1ac2fa17409ac3228f87eb71c99ce9e725521
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780871"
---
# <a name="simplified-embedding"></a>Basitleştirilmiş Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Basitleştirilmiş ekleme, belge görünümü nesnesi için üst öğe olduğunda (yani, bir alt öğesi yapıldığında) düzenleyicide etkinleştirilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> arabirim pencere komutlarını işlemek için uygulanır. Basitleştirilmiş ekleme düzenleyicileri etkin denetimleri barındıraamaz. Basitleştirilmiş ekleme ile bir düzenleyici oluşturmak için kullanılan nesneler aşağıdaki çizimde gösterilmiştir.  
  
 ![Basitleştirilmiş ekleme Düzenleyicisi grafiği](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
Basitleştirilmiş ekleme ile düzenleyici  
  
> [!NOTE]
> Bu çizimdeki nesnelerden yalnızca `CYourEditorFactory` nesne, standart dosya tabanlı bir düzenleyici oluşturmak için gereklidir. Özel bir düzenleyici oluşturuyorsanız, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> düzenleyiciniz büyük olasılıkla kendi özel Kalıcılık mekanizmasına sahip olacağı için uygulamanız gerekmez. Ancak özel olmayan düzenleyiciler için bunu yapmanız gerekir.  
  
 Basitleştirilmiş katıştırma ile bir düzenleyici oluşturmak için uygulanan tüm arabirimler, nesnesine dahil edilir `CYourEditorDocument` . Ancak, belge verilerinin birden çok görünümünü desteklemek için, arabirimleri ayrı verilere ayırın ve aşağıdaki tabloda gösterildiği gibi nesneleri görüntüleyin.  
  
|Arabirim|Arabirimin konumu|Kullanın|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Görünüm|Üst pencereye bağlantı sağlar.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Görünüm|Komutları işler.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Görünüm|Durum çubuğu güncelleştirmelerini etkinleştirilir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Görünüm|**Araç kutusu** öğelerini etkinleştirilir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Veriler|Dosya değiştiğinde bildirim gönderir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Veriler|Dosya türü için farklı Kaydet özelliğini sunar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Veriler|Belge için kalıcılığı mümkün hale getirme.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Veriler|Yeniden yükleme tetikleme gibi dosya değişiklik olaylarının gizlenme olanağı sağlar.|
