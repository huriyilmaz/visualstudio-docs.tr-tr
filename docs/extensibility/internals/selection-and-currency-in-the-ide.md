---
title: IDE 'de seçim ve para birimi | Microsoft Docs
description: VSPackages 'ın para birimi izlemede nasıl bir parçası olduğunu öğrenin. Visual Studio IDE, seçim bağlamını kullanarak şu anda seçili nesneler hakkında bilgi tutar.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b2d745619be8bff77503bc14a1d7a87d84cc7864
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875603"
---
# <a name="selection-and-currency-in-the-ide"></a>IDE’de Seçim ve Para Birimi
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Tümleşik geliştirme ortamı (IDE), kullanıcıların seçilmiş olan nesneler hakkında seçim *bağlamını* kullanarak bilgi saklar. Seçim bağlamında VSPackages, para birimi izlemede iki şekilde bir parçası alabilir:

- IDE 'ye VSPackages hakkında para birimi bilgilerini yayarak.

- Kullanıcılar, IDE içindeki şu anda etkin olan seçimleri izleyerek.

## <a name="selection-context"></a>Seçim bağlamı
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE genel olarak IDE para birimini kendi genel seçim bağlamı nesnesinde izler. Aşağıdaki tabloda seçim bağlamını oluşturan öğeler gösterilmektedir.

|Öğe|Açıklama|
|-------------|-----------------|
|Geçerli hiyerarşi|Genellikle geçerli proje; BOŞ bir geçerli hiyerarşi, çözümün bir bütün olarak güncel olduğunu gösterir.|
|Geçerli öğe kimliği|Geçerli hiyerarşi içindeki seçili öğe; Proje penceresinde birden çok seçim olduğunda, birden çok geçerli öğe olabilir.|
|Geçerli `SelectionContainer`|Özellikler penceresi özellikleri görüntülemesi gereken bir veya daha fazla nesneyi tutar.|

 Ayrıca, ortam iki genel liste tutar:

- Etkin UI komut tanımlayıcılarının listesi

- Şu anda etkin olan öğe türlerinin listesi.

### <a name="window-types-and-selection"></a>Pencere türleri ve seçimi
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE pencereleri iki genel türe göre düzenler:

- Hiyerarşi türü pencereler

- Araç ve belge pencereleri gibi çerçeve pencereleri

  IDE, para birimini bu pencere türlerinin her biri için farklı izler.

  En yaygın proje türü pencere, IDE 'nin denetlediği Çözüm Gezgini ' dir. Proje türü bir pencere, genel seçim bağlamının genel hiyerarşisini ve öğe sayısını izler ve pencere, geçerli hiyerarşiyi belirlemede kullanıcının seçimine bağlıdır. Proje türü Windows için, ortam, <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> VSPackages 'ın açık öğelerin geçerli değerlerini izleyebileceği genel hizmeti sağlar. Ortamdaki özellik göz atma özelliği bu genel hizmet tarafından yönlendiriliyor.

  Çerçeve pencereleri, diğer yandan, SelectionContext değerini (hiyerarşi/ItemId/SelectionContainer trio) göndermek için çerçeve penceresi içindeki DocObject ' i kullanın. . Çerçeve pencereleri <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Bu amaçla hizmeti kullanır. DocObject, yalnızca seçim kapsayıcısına ait değerleri gönderebilir, bu, MDI alt belgeleri için tipik olduğu gibi, hiyerarşi ve öğe için yerel değerleri değişmeden bırakır.

### <a name="events-and-currency"></a>Olaylar ve para birimi
 Ortamın para birimi kavramını etkileyen iki tür olay meydana gelebilir:

- Genel düzeye yayılan ve pencere çerçevesi seçim bağlamını değiştiren olaylar. Bu tür bir olay örnekleri, açılan bir MDI alt penceresi, açılan bir araç penceresi veya açılan bir proje türü araç penceresi içerir.

- Pencere çerçevesi seçim bağlamı içinde izlenen öğeleri değiştiren olaylar. Örnek olarak, bir DocObject içindeki seçimi değiştirme veya bir proje türü penceresinde seçimi değiştirme sayılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Seçim Bağlamı Nesneleri](../../extensibility/internals/selection-context-objects.md)
- [Kullanıcıya Geri Bildirim](../../extensibility/internals/feedback-to-the-user.md)
