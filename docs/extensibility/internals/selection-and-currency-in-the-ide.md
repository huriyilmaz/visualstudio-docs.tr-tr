---
title: IDE'de Seçim ve Para Birimi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f580b7c8e1651dcbcd053476ae756399a0ac3482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705577"
---
# <a name="selection-and-currency-in-the-ide"></a>IDE’de Seçim ve Para Birimi
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı (IDE), seçim *bağlamını*kullanarak kullanıcıların şu anda seçili nesneleri hakkında bilgi tutar. Seçim bağlamında, VSPackages para birimi takibinde iki şekilde katılabilir:

- VSPackages hakkında para birimi bilgilerini IDE'ye yayarak.

- IDE içinde kullanıcıların şu anda etkin seçimlerini izleyerek.

## <a name="selection-context"></a>Seçim Bağlamı
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, ide para birimini kendi küresel seçim bağlamında takip eder. Aşağıdaki tablo, seçim bağlamını oluşturan öğeleri gösterir.

|Öğe|Açıklama|
|-------------|-----------------|
|Geçerli hiyerarşi|Genellikle geçerli proje; NULL geçerli hiyerarşisi, çözümün bir bütün olarak geçerli olduğunu gösterir.|
|Geçerli ItemID|Geçerli hiyerarşi içinde seçili öğe; proje penceresinde birden çok seçim olduğunda, birden çok geçerli öğe olabilir.|
|Şu anki`SelectionContainer`|Özellikler penceresinin özelliklerini görüntülemesi gereken bir veya daha fazla nesneyi tutar.|

 Ayrıca, ortam iki genel liste tutar:

- Etkin UI komut tanımlayıcılarının listesi

- Şu anda etkin öğe türlerinin listesi.

### <a name="window-types-and-selection"></a>Pencere Türleri ve Seçimi
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE pencereleri iki genel türde düzenler:

- Hiyerarşi tipi pencereler

- Araç ve belge pencereleri gibi çerçeve pencereleri

  IDE, bu pencere türlerinin her biri için para birimini farklı izler.

  En yaygın proje türü penceresi, IDE'nin denetlediği çözüm gezginidir. Proje türü penceresi, genel seçim bağlamının genel hiyerarşisini ve ItemID'sini izler ve pencere geçerli hiyerarşiyi belirlemek için kullanıcının seçimine dayanır. Proje türü pencereler için ortam, VSPackages'in açık öğeler için geçerli değerleri izleyerek küresel hizmeti <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>sağlar. Çevrede özellik tarama bu küresel hizmet tarafından tahrik edilir.

  Çerçeve pencereleri ise, SelectionContext değerini (hiyerarşi/ItemID/SelectionContainer üçlüsü) zorlamak için çerçeve penceresi içindeki DocObject'i kullanın. . Çerçeve pencereleri <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> hizmeti bu amaç için kullanır. DocObject, MDI alt belgeleri için tipik olduğu gibi hiyerarşi ve ItemID için yerel değerleri değişmeden bırakarak yalnızca seçim kapsayıcısı için değerleri zorlayabilir.

### <a name="events-and-currency"></a>Olaylar ve Para Birimi
 Ortamın para birimi kavramını etkileyen iki tür olay oluşabilir:

- Genel düzeye yayılan ve pencere çerçevesi seçim bağlamını değiştiren olaylar. Bu tür bir olaya örnek olarak bir MDI Alt penceresi açılır, genel bir araç penceresi açılır veya proje türü araç penceresi açılır.

- Pencere çerçevesi seçim bağlamında izlenen öğeleri değiştiren olaylar. Örnek olarak, DocObject içindeki seçimi değiştirme veya proje türü penceresinde seçimi değiştirme sayılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Seçim Bağlamı Nesneleri](../../extensibility/internals/selection-context-objects.md)
- [Kullanıcıya Geri Bildirim](../../extensibility/internals/feedback-to-the-user.md)
