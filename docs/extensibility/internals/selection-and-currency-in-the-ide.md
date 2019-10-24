---
title: IDE 'de seçim ve para birimi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edff400420ca5f0c93e1df85fb9118eee6302d02
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723959"
---
# <a name="selection-and-currency-in-the-ide"></a>IDE’de Seçim ve Para Birimi
@No__t_0 tümleşik geliştirme ortamı (IDE), kullanıcıların şu anda seçili nesneleri hakkındaki bilgileri seçim *bağlamını*kullanarak tutar. Seçim bağlamında VSPackages, para birimi izlemede iki şekilde bir parçası alabilir:

- IDE 'ye VSPackages hakkında para birimi bilgilerini yayarak.

- Kullanıcılar, IDE içindeki şu anda etkin olan seçimleri izleyerek.

## <a name="selection-context"></a>Seçim bağlamı
 @No__t_0 IDE genel olarak kendi genel seçim bağlamı nesnesinde IDE para birimini izler. Aşağıdaki tabloda seçim bağlamını oluşturan öğeler gösterilmektedir.

|Öğe|Açıklama|
|-------------|-----------------|
|Geçerli hiyerarşi|Genellikle geçerli proje; BOŞ bir geçerli hiyerarşi, çözümün bir bütün olarak güncel olduğunu gösterir.|
|Geçerli öğe kimliği|Geçerli hiyerarşi içindeki seçili öğe; Proje penceresinde birden çok seçim olduğunda, birden çok geçerli öğe olabilir.|
|Geçerli `SelectionContainer`|Özellikler penceresi özellikleri görüntülemesi gereken bir veya daha fazla nesneyi tutar.|

 Ayrıca, ortam iki genel liste tutar:

- Etkin UI komut tanımlayıcılarının listesi

- Şu anda etkin olan öğe türlerinin listesi.

### <a name="window-types-and-selection"></a>Pencere türleri ve seçimi
 @No__t_0 IDE pencereleri iki genel türe göre düzenler:

- Hiyerarşi türü pencereler

- Araç ve belge pencereleri gibi çerçeve pencereleri

  IDE, para birimini bu pencere türlerinin her biri için farklı izler.

  En yaygın proje türü pencere, IDE 'nin denetlediği Çözüm Gezgini ' dir. Proje türü bir pencere, genel seçim bağlamının genel hiyerarşisini ve öğe sayısını izler ve pencere, geçerli hiyerarşiyi belirlemede kullanıcının seçimine bağlıdır. Proje türü Windows için ortam, VSPackages 'ın açık öğelerin geçerli değerlerini izleyebileceği genel hizmet <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> sağlar. Ortamdaki özellik göz atma özelliği bu genel hizmet tarafından yönlendiriliyor.

  Çerçeve pencereleri, diğer yandan, SelectionContext değerini (hiyerarşi/ItemId/SelectionContainer trio) göndermek için çerçeve penceresi içindeki DocObject ' i kullanın. biçimindeki telefon numarasıdır. Çerçeve pencereleri bu amaçla hizmet <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> kullanır. DocObject, yalnızca seçim kapsayıcısına ait değerleri gönderebilir, bu, MDI alt belgeleri için tipik olduğu gibi, hiyerarşi ve öğe için yerel değerleri değişmeden bırakır.

### <a name="events-and-currency"></a>Olaylar ve para birimi
 Ortamın para birimi kavramını etkileyen iki tür olay meydana gelebilir:

- Genel düzeye yayılan ve pencere çerçevesi seçim bağlamını değiştiren olaylar. Bu tür bir olay örnekleri, açılan bir MDI alt penceresi, açılan bir araç penceresi veya açılan bir proje türü araç penceresi içerir.

- Pencere çerçevesi seçim bağlamı içinde izlenen öğeleri değiştiren olaylar. Örnek olarak, bir DocObject içindeki seçimi değiştirme veya bir proje türü penceresinde seçimi değiştirme sayılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Seçim Bağlamı Nesneleri](../../extensibility/internals/selection-context-objects.md)
- [Kullanıcıya Geri Bildirim](../../extensibility/internals/feedback-to-the-user.md)