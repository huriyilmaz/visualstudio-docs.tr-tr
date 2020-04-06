---
title: Basitleştirilmiş Katıştırma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9bc9619ae1ed75aed3656ff014296f7c7d88fa0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700082"
---
# <a name="simplified-embedding"></a>Basitleştirilmiş Ekleme
Basitleştirilmiş katıştırma, belge görünümü nesnesi ana öğeye (diğer bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]deyişle, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> bir alt öğeye sahip olunduğunda) ve arabirim pencere komutlarını işlemek için uygulandığında bir düzenleyicide etkinleştirilir. Basitleştirilmiş katıştırma düzenleyicileri etkin denetimleri barındıramaz. Basitleştirilmiş katıştırma ile bir düzenleyici oluşturmak için kullanılan nesneler aşağıdaki resimde gösterilmiştir.

 ![Basitleştirilmiş Katıştırma Düzenleyicisi grafiği](../extensibility/media/vssimplifiedembeddingeditor.gif "vsBasitdEmbeddingEditor") Basitleştirilmiş gömme ile düzenleyici

> [!NOTE]
> Bu çizimdeki nesnelerden, standart `CYourEditorFactory` bir dosya tabanlı düzenleyici oluşturmak için yalnızca nesne gereklidir. Özel bir düzenleyici oluşturuyorsanız, düzenleyiciniz büyük <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>olasılıkla kendi özel kalıcılık mekanizmasına sahip olacağından, uygulamanız gerekmez. Ancak, özel olmayan editörler için bunu yapmanız gerekir.

 Basitleştirilmiş katıştırma ile bir düzenleyici oluşturmak için `CYourEditorDocument` uygulanan tüm arabirimler nesnede bulunur. Ancak, belge verilerinin birden çok görünümünü desteklemek için arabirimleri ayrı verilere bölün ve aşağıdaki tabloda belirtildiği gibi nesneleri görüntüleyin.

|Arabirim|Arabirimin konumu|Kullanım|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Görüntüle|Üst pencereye bağlantı sağlar.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Görüntüle|Komutları işler.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Görüntüle|Durum çubuğu güncelleştirmelerini sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Görüntüle|Araç **Kutusu** öğelerini etkinleştirir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Veriler|Dosya değiştiğinde bildirim gönderir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Veriler|Dosya türü için Farklı Kaydet özelliğini etkinleştirir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Veriler|Belge için kalıcılığı sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Veriler|Yeniden yükleme tetikleyicisi gibi dosya değişikliği olaylarının bastırılmasına izin verir.|
