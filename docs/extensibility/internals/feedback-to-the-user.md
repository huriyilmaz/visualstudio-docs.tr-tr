---
title: User | Microsoft Docs
description: Tümleşik geliştirme ortamında (IDE) kullanıcıya kullanılabilir işlevler hakkında görsel geri Visual Studio sağlamayı öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626133"
---
# <a name="feedback-to-the-user"></a>Kullanıcıya geri bildirim
Tümleşik geliştirme ortamında (IDE), kullanılabilir işlevlerle ilgili görsel geri bildirim kullanıcının geçerli seçimine ve genel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seçim bağlamına göredir. Aşağıdaki tabloda, farklı seçim bağlamlarında kullanılabilen işlevler listelemektedir.

|Seçim bağlamı|Kullanılabilir işlevsellik|
|-----------------------|-----------------------------|
|IDE|Genel|
|Geçerli ürün kümesi|Ürüne özgü|
|Etkin hiyerarşi|Hiyerarşi türüne özgü|
|Etkin hiyerarşi öğesi|Hiyerarşi öğe türüne özgü|
|Etkin belge|Belge türüne özgü|
|En üstteki çok belgeli arabirim (MDI) penceresi|Pencere türüne özgü|
|Geçerli seçim bağlamı|Seçim bağlamına özgü|

 Yalnızca kullanıcıların ihtiyacı olan işlevselliği ortaya çıkararak tutarlı seçim ve ortam bağlamı geri bildirimi sağlarsanız, IDE'nin karmaşıklığını azaltırsınız. IDE'de bir pencere açıldığında aşağıdaki kurallar geçerlidir:

- Pencere seçim bağlamını değiştirirse, pencerede seçim geri bildirimi açıkça  gösterilir ve gösteriliyorsa Dinamik Yardım penceresi geçerli bağlamı yansıtacak şekilde güncelleştirilir.

- Pencere genel seçim bağlamını değiştirirse, bağlama özgü tüm menüler, etkin hiyerarşi penceresi ve uygulama başlık çubuğu geçerli bağlamı yansıtacak şekilde güncelleştirilir.

- Pencere, Özellikler penceresinde ve isteğe  bağlı olarak, gösteriliyorsa Özellik Sayfaları iletişim kutusunda geçerli **seçimin özelliklerini ortaya** çıkartır.

- Pencere özellikleri ortaya çıkaramaz veya genel seçim bağlamını değiştirmiyorsa, IDE'de artık etkin pencere olmadığı zaman seçim geri bildirimi pencerede kalmamalı.

- Belgeye özgü tüm araç pencereleri sürekli olarak etkin belgeyi yansıtmalı.

- Menüler, araç çubukları ve uygulama başlık çubuğu en üstteki çok belgeli arabirim (MDI) istemci penceresini yansıtabilir.

  Örneğin, bir Web Uygulaması projesinin içindeki **bir Web** Formunun HTML Visual Basic açıldığında ve kullanıcı bir etiket seçerse, geri bildirim şu `<td>` şekilde sağlanır:

- Seçim etkin pencerede gösterilir ve Özellikler penceresine **yansıtıldı.**

- Belgeye özgü **Araç Kutusu,** etkin belgeyi yansıtacak şekilde güncelleştirilir.

- Düzenleyici **araç** çubuğu **ve Tablo** menüsü görüntülenir ve başlık çubuğu Web Formu penceresini yansıtacak şekilde görüntülenebilir.

- Genellikle Çözüm Gezgini olan etkin hiyerarşi penceresi ve başlık çubuğu geçerli bağlamı yansıtacak şekilde güncelleştirmesi ve bağlama duyarlı **Project** menü komutları artık etkin Web Uygulaması projesi için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDE'de seçim ve para birimi](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md)
- [Hiyerarşiler ve seçim](../../extensibility/internals/hierarchies-and-selection.md)
