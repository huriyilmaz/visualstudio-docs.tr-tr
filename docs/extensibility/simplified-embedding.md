---
title: Basitleştirilmiş Ekleme | Microsoft Docs
description: Belge görünümü nesnesi bir düzenleyicinin alt nesnesi olduğunda düzenleyicide etkinleştirilebilir olan basitleştirilmiş ekleme hakkında Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ea5186872232f3c84ac41567938ea5822915746b37adafffe7263077d3c87b43
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121260377"
---
# <a name="simplified-embedding"></a>Basitleştirilmiş Ekleme
Basitleştirilmiş ekleme, belge görünümü nesnesinin üst öğesi (yani alt öğesi) olduğunda düzenleyicide etkinleştirilir ve pencere komutlarını işlemek için arabirim [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> uygulanır. Basitleştirilmiş ekleme düzenleyicileri etkin denetimleri barındıramaz. Basitleştirilmiş ekleme ile düzenleyici oluşturmak için kullanılan nesneler aşağıdaki çizimde gösterilmiştir.

 ![Basitleştirilmiş Ekleme Düzenleyicisi grafiği](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Basitleştirilmiş ekleme ile düzenleyici

> [!NOTE]
> Bu çizimdeki nesnelerin standart dosya `CYourEditorFactory` tabanlı bir düzenleyici oluşturmak için yalnızca nesnesi gereklidir. Özel bir düzenleyici oluşturuyorsanız, büyük olasılıkla kendi özel kalıcılık mekanizmasına sahip olduğundan, uygulaması <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> gerekmez. Ancak, özel olmayan düzenleyiciler için bunu yapmak gerekir.

 Basitleştirilmiş ekleme ile bir düzenleyici oluşturmak için uygulanan tüm arabirimler nesnesinde `CYourEditorDocument` yer almaktadır. Ancak, belge verisi birden çok görünümünü desteklemek için, arabirimleri ayrı verilere bölün ve nesneleri aşağıdaki tabloda gösterilen şekilde görüntülendi.

|Arabirim|Arabirimin konumu|Kullanın|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Görünüm|Üst pencereye bağlantı sağlar.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Görünüm|Komutları işleme.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Görünüm|Durum çubuğu güncelleştirmelerini sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Görünüm|Araç **Kutusu öğelerini** sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Veriler|Dosya değişirken bildirim gönderir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Veriler|Bir dosya türü için Farklı Kaydet özelliğini sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Veriler|Belge için kalıcılığı sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Veriler|Yeniden yükleme tetiklemesi gibi dosya değişikliği olaylarının gizlenmesine izin verir.|
