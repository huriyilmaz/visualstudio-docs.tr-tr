---
title: IDE'de Seçim ve Para Birimi | Microsoft Docs
description: VSPackage'ların para birimi izlemeye nasıl katıldıklarını öğrenin. IDE Visual Studio seçili nesnelerle ilgili bilgileri seçim bağlamını kullanarak sürdürür.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e167d963592e6f555082978c07d3fd7a70cb5fa82636864f5518665bffc6d38f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275196"
---
# <a name="selection-and-currency-in-the-ide"></a>IDE’de Seçim ve Para Birimi
Tümleşik [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geliştirme ortamı (IDE), seçim bağlamını kullanarak kullanıcıların seçili nesneleri hakkında bilgi *sağlar.* Seçim bağlamıyla VSPackage'lar para birimi izleme kapsamında iki şekilde yer alır:

- VSPackage'lar hakkında para birimi bilgilerini IDE'ye yayarak.

- Kullanıcıların IDE'de şu anda etkin olan seçimlerini izleme.

## <a name="selection-context"></a>Seçim Bağlamı
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE, kendi genel seçim bağlamı nesnesinde IDE para birimini genel olarak takip eder. Aşağıdaki tabloda seçim bağlamını ortaya koyan öğeler yer alır.

|Öğe|Açıklama|
|-------------|-----------------|
|Geçerli hiyerarşi|Genellikle geçerli proje; NULL geçerli hiyerarşisi, çözümün bir bütün olarak geçerli olduğunu gösterir.|
|Geçerli ItemID|Geçerli hiyerarşi içinde seçilen öğe; bir proje penceresinde birden çok seçim olduğunda, birden çok geçerli öğe olabilir.|
|Şu anki `SelectionContainer`|Uygulamanın özelliklerini görüntülemesi gereken bir Özellikler penceresi daha fazla nesne tutar.|

 Buna ek olarak, ortam iki genel liste bulundurmaktadır:

- Etkin kullanıcı arabirimi komut tanımlayıcılarının listesi

- Şu anda etkin olan öğe türlerinin listesi.

### <a name="window-types-and-selection"></a>Pencere Türleri ve Seçimi
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE, pencereleri iki genel türe göre düzenleyebilir:

- Hiyerarşi türü pencereler

- Araç ve belge pencereleri gibi çerçeve pencereleri

  IDE, bu pencere türlerinin her biri için para birimini farklı izler.

  En yaygın proje türü penceresi, IDE'nin denetiminde olduğu çözüm gezginidir. Proje türü bir pencere, genel seçim bağlamının genel hiyerarşisini ve ItemID'sini izler ve pencere geçerli hiyerarşiyi belirlemek için kullanıcının seçimine bağlı olur. Proje türü pencereleri için ortam, VSPackage'ların açık öğeler için geçerli değerleri <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> izleyene genel hizmeti sağlar. Ortamda özellik tarama bu genel hizmet tarafından çalıştırılır.

  Öte yandan çerçeve pencereleri, SelectionContext değerini (hierarchy/ItemID/SelectionContainer üçlüsü) itmek için çerçeve penceresindeki DocObject öğesini kullanın. . Çerçeve pencereleri bu amaçla <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> hizmeti kullanır. DocObject, MDI alt belgelerinde olduğu gibi hiyerarşi ve ItemID için yerel değerleri değiştirmeden bırakarak yalnızca seçim kapsayıcısı için değerleri iter.

### <a name="events-and-currency"></a>Olaylar ve Para Birimi
 Ortamın para birimini etkileyen iki tür olay oluşabilir:

- Genel düzeye yayma ve pencere çerçevesi seçim bağlamını değiştirme olayları. Bu tür bir olayın örnekleri arasında açılan MDI Alt Penceresi, açılan genel bir araç penceresi veya açılan proje türü araç penceresi yer atılır.

- Pencere çerçevesi seçim bağlamı içinde izleme yapılan öğeleri değiştiren olaylar. Örnek olarak DocObject içindeki seçimi değiştirme veya proje türü penceresinde seçimi değiştirme örnek olarak verilmiştir.

## <a name="see-also"></a>Ayrıca bkz.
- [Seçim Bağlamı Nesneleri](../../extensibility/internals/selection-context-objects.md)
- [Kullanıcıya Geri Bildirim](../../extensibility/internals/feedback-to-the-user.md)
