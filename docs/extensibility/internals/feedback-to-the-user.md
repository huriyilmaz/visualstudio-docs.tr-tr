---
title: Kullanıcıya geri bildirim | Microsoft Docs
description: Visual Studio tümleşik geliştirme ortamında (ıde) kullanılabilir işlevsellik hakkında kullanıcıya görsel geri bildirim sağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: be19f6bb9b1879746542d73e67f6b77b0d28d792
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102733"
---
# <a name="feedback-to-the-user"></a>Kullanıcıya geri bildirim
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Tümleşik geliştirme ortamında (IDE), kullanılabilir işlevlerle ilgili görsel geri bildirimler kullanıcının geçerli seçimine ve genel seçim içeriğine göre belirlenir. Aşağıdaki tabloda, farklı seçim bağlamlarında kullanılabilen işlevler listelenmektedir.

|Seçim bağlamı|Kullanılabilir işlevsellik|
|-----------------------|-----------------------------|
|IDE|Genel|
|Geçerli ürün kümesi|Ürüne özgü|
|Etkin hiyerarşi|Hiyerarşi türüne özgü|
|Etkin hiyerarşi öğesi|Hiyerarşi öğesi türüne özgü|
|Etkin belge|Belge türüne özgü|
|En üstteki çoklu belge arabirimi (MDI) penceresi|Pencere türüne özgü|
|Geçerli seçim bağlamı|Seçim bağlamı özel|

 Yalnızca kullanıcıların ihtiyacı olan işlevleri ve sürekli olarak tutarlı seçim ve ortam bağlamı geri bildirimi sağlamak istiyorsanız IDE 'deki karmaşıklığı azaltabilirsiniz. IDE 'de bir pencere her açıldığında aşağıdaki kurallar geçerlidir:

- Pencere seçim bağlamını değiştirirse, pencerede seçim geri bildirimi açıkça belirtilir ve gösterilen **dinamik yardım** penceresi, geçerli bağlamı yansıtacak şekilde güncelleştirilir.

- Pencere, genel seçim bağlamını değiştirirse, içeriğe özgü tüm menüler, etkin hiyerarşi penceresi ve uygulama başlık çubuğu geçerli bağlamı yansıtacak şekilde güncelleştirilir.

- Pencere, **Özellikler** penceresinde geçerli seçimin özelliklerini ve isteğe bağlı olarak, **Özellik sayfaları** iletişim kutusunu göstermek zorunda olmalıdır.

- Pencere özellikleri göstermez veya genel seçim bağlamını değiştirmezse, artık IDE 'de etkin pencere olmadığında seçim geri bildirimi pencerede kalmaz.

- Belgeye özgü tüm araç pencereleri sürekli olarak etkin belgeyi yansıtmalıdır.

- Menüler, araç çubukları ve uygulama başlık çubuğu, en üstteki çoklu belge arabirimi (MDI) istemci penceresini yansıtmalıdır.

  örneğin, bir Visual Basic web uygulaması projesi içindeki bir **web formunun** HTML görünümü açıldığında ve kullanıcı bir `<td>` etiketi seçtiğinde, aşağıdaki şekilde geri bildirim sağlanır:

- Seçim etkin pencerede gösterilir ve **Özellikler** penceresinde yansıtılır.

- Belgeye özgü **araç kutusu** etkin belgeyi yansıtacak şekilde güncelleştirilir.

- **Düzenleyici** araç çubuğu ve **tablo** menüsü görüntülenir ve başlık çubuğu Web formu penceresini yansıtacak şekilde güncelleştirilir.

- genellikle **Çözüm Gezgini** olan etkin hiyerarşi penceresi ve geçerli bağlamı yansıtmak için başlık çubuğu güncelleştirmesi ve bağlam duyarlı **Project** menü komutları artık etkin Web uygulaması projesi için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDE 'de seçim ve para birimi](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md)
- [Hiyerarşiler ve seçim](../../extensibility/internals/hierarchies-and-selection.md)
