---
title: Basitleştirilmiş ekleme | Microsoft Docs
description: Belge görünümü nesnesi Visual Studio 'nun bir alt öğesi olduğunda düzenleyicide etkinleştirilebilen, Basitleştirilmiş ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f62e3a4f33193f36e76b1286ae3d35d26706b3ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928100"
---
# <a name="simplified-embedding"></a>Basitleştirilmiş Ekleme
Basitleştirilmiş ekleme, belge görünümü nesnesi için üst öğe olduğunda (yani, bir alt öğesi yapıldığında) düzenleyicide etkinleştirilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> arabirim pencere komutlarını işlemek için uygulanır. Basitleştirilmiş ekleme düzenleyicileri etkin denetimleri barındıraamaz. Basitleştirilmiş ekleme ile bir düzenleyici oluşturmak için kullanılan nesneler aşağıdaki çizimde gösterilmiştir.

 ![Basitleştirilmiş ekleme Düzenleyicisi grafiği](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Basitleştirilmiş ekleme ile düzenleyici

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
