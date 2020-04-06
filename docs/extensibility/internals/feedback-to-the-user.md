---
title: Kullanıcıya Geri Bildirim | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46b9190b16b9aa444384847bf209ccca50c7f768
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708408"
---
# <a name="feedback-to-the-user"></a>Kullanıcıya geri bildirim
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamında (IDE), kullanılabilir işlevsellikle ilgili görsel geri bildirimler kullanıcının mevcut seçimine ve genel seçim bağlamına dayanır. Aşağıdaki tabloda, farklı seçim bağlamlarında kullanılabilen işlevsellik listelenir.

|Seçim bağlamı|Kullanılabilir işlevsellik|
|-----------------------|-----------------------------|
|IDE|Genel|
|Geçerli ürün seti|Ürüne özel|
|Etkin hiyerarşi|Hiyerarşi türüne özgü|
|Etkin hiyerarşi öğesi|Hiyerarşi öğesi türüne özgü|
|Etkin belge|Belge türüne özgü|
|En çok belge arabirimi (MDI) penceresi|Pencere türüne özgü|
|Geçerli seçim bağlamı|Seçim bağlamına özgü|

 Yalnızca kullanıcıların gereksinim duyduğu işlevselliği ortaya çıkarır ve sürekli olarak tutarlı seçim ve ortam bağlamı geri bildirimi sağlarsanız, IDE'deki karmaşıklığı azaltırsınız. IDE'de bir pencere açıldığında aşağıdaki kurallar geçerlidir:

- Pencere seçim bağlamını değiştirirse, seçim geri bildirimi pencerede açıkça gösterilir ve gösterildiği takdirde **Dinamik Yardım** penceresi geçerli bağlamı yansıtacak şekilde güncelleştirilir.

- Pencere genel seçim bağlamını değiştirirse, tüm içeriğe özgü menüler, etkin hiyerarşi penceresi ve uygulama başlığı çubuğu geçerli bağlamı yansıtacak şekilde güncelleştirilir.

- Pencere, **Özellikler** penceresindeki geçerli seçimin özelliklerini ve gösterildiği takdirde **Özellik Sayfaları** iletişim kutusunu isteğe bağlı olarak yüzeye çıkarmalıdır.

- Pencere özellikleri yüzeyine çıkarmazsa veya genel seçim bağlamını değiştirmiyorsa, Seçim geri bildirimi Artık IDE'deki etkin pencere olmadığında pencerede kalmamalıdır.

- Belgeye özel tüm araç pencereleri etkin belgeyi sürekli olarak yansıtmalıdır.

- Menüler, araç çubukları ve uygulama başlığı çubuğu en üstteki çoklu belge arabirimi (MDI) istemci penceresini yansıtmalıdır.

  Örneğin, Visual Basic Web Application projesiiçindeki bir **Web Formunun** HTML görünümü açıldığında `<td>` ve kullanıcı bir etiket seçtiğinde, geri bildirim aşağıdaki şekilde sağlanır:

- Seçim etkin pencerede gösterilir ve **Özellikler** penceresine yansıtılır.

- Belgeye özel **Araç Kutusu,** etkin belgeyi yansıtacak şekilde güncelleştirilir.

- **Düzenleyici** araç çubuğu ve **Tablo** menüsü görüntülenir ve başlık çubuğu Web Formu penceresini yansıtacak şekilde güncellenir.

- Genellikle **Çözüm Gezgini**olan etkin hiyerarşi penceresi ve geçerli bağlamı ve içeriğe duyarlı **Project** menüsü komutlarını yansıtacak şekilde başlık çubuğu güncelleştirmesi artık etkin Web Uygulaması projesiiçin geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDE'de seçim ve para birimi](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md)
- [Hiyerarşiler ve seçim](../../extensibility/internals/hierarchies-and-selection.md)
